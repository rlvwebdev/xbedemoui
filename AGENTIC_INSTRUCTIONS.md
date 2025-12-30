# Agentic Instructions for Single-Page HTML Examples

## Overview
These instructions define the standards and requirements for creating semantic, compliant, and well-structured single-page HTML files with embedded CSS and JavaScript. Each example should be self-contained, accessible, and follow modern web standards.

---

## File Structure Requirements

### 1. Single-File Architecture
- Each example MUST be a standalone HTML file
- CSS MUST be embedded in `<style>` tags within `<head>`
- JavaScript MUST be embedded in `<script>` tags before closing `</body>`
- No external dependencies unless absolutely necessary (prefer vanilla solutions)
- File naming convention: `example-[descriptive-name].html`

### 2. Document Structure
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <!-- Meta tags -->
    <!-- Title -->
    <!-- Embedded CSS -->
  </head>
  <body>
    <!-- Semantic HTML content -->
    <!-- Embedded JavaScript -->
  </body>
</html>
```

---

## HTML Standards

### 1. Document Declaration & Language
- Always start with `<!DOCTYPE html>`
- Include `lang` attribute on `<html>` tag (e.g., `lang="en"`)
- Use UTF-8 character encoding: `<meta charset="UTF-8">`

### 2. Essential Meta Tags
Required meta tags in `<head>`:
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="[Brief description of the example]">
<title>[Descriptive Page Title]</title>
```

### 3. Semantic HTML5 Elements
Use appropriate semantic elements:
- `<header>` - Page or section header
- `<nav>` - Navigation links
- `<main>` - Main content (only one per page)
- `<article>` - Self-contained content
- `<section>` - Thematic grouping of content
- `<aside>` - Tangentially related content
- `<footer>` - Page or section footer
- `<figure>` and `<figcaption>` - Images with captions
- `<time>` - Dates and times with `datetime` attribute

### 4. Accessibility Requirements
- All images MUST have meaningful `alt` attributes
- Use proper heading hierarchy (`<h1>` → `<h2>` → `<h3>`, no skipping)
- Only one `<h1>` per page
- Form inputs MUST have associated `<label>` elements
- Interactive elements MUST be keyboard accessible
- Use `aria-label` or `aria-labelledby` when visible labels aren't present
- Color contrast ratios MUST meet WCAG AA standards (4.5:1 for normal text)
- Focus indicators MUST be visible
- Use `role` attributes when semantic HTML isn't sufficient

### 5. Form Best Practices
```html
<form>
  <label for="input-id">Label Text:</label>
  <input type="text" id="input-id" name="input-name" required>
  
  <button type="submit">Submit</button>
</form>
```
- Always pair `<label>` with `for` attribute matching input `id`
- Use appropriate input types (`email`, `tel`, `number`, `date`, etc.)
- Include `required`, `pattern`, `min`, `max` attributes for validation
- Use `<fieldset>` and `<legend>` for grouping related inputs

### 6. Avoid Non-Semantic Elements
- Minimize use of `<div>` and `<span>` - prefer semantic alternatives
- Use semantic elements even when styling requirements seem simpler with divs
- Only use `<div>` for pure layout or styling needs without semantic meaning

---

## CSS Standards

### 1. Embedding Location
- All CSS MUST be in a `<style>` tag within `<head>`
- Use CSS comments to organize sections

### 2. CSS Organization
```css
/* ==================
   CSS Reset / Base Styles
   ================== */

/* ==================
   Layout
   ================== */

/* ==================
   Components
   ================== */

/* ==================
   Utilities
   ================== */

/* ==================
   Responsive Design
   ================== */
```

### 3. Modern CSS Practices
- Use CSS custom properties (variables) for colors, spacing, and reusable values
```css
:root {
  --primary-color: #007bff;
  --secondary-color: #6c757d;
  --font-family: system-ui, -apple-system, sans-serif;
  --spacing-unit: 8px;
  --border-radius: 4px;
}
```

- Use Flexbox and CSS Grid for layouts (avoid floats)
- Use relative units (`rem`, `em`, `%`, `vh`, `vw`) over fixed pixels
- Implement mobile-first responsive design
- Use `box-sizing: border-box` globally

### 4. Naming Conventions
- Use BEM (Block Element Modifier) or consistent semantic class names
- Use lowercase and hyphens: `.card-header`, `.btn-primary`
- Avoid overly generic names like `.text` or `.box`

### 5. Responsive Design
- Include responsive breakpoints using media queries
```css
/* Mobile first - base styles for mobile */

@media (min-width: 768px) {
  /* Tablet styles */
}

@media (min-width: 1024px) {
  /* Desktop styles */
}
```

### 6. Visual Hierarchy & Spacing
- Maintain consistent spacing using spacing variables
- Use adequate whitespace for readability
- Ensure sufficient color contrast for accessibility
- Use appropriate font sizes (minimum 16px for body text)

---

## JavaScript Standards

### 1. Embedding Location
- Place `<script>` tags just before closing `</body>` tag
- Alternatively, use `<script defer>` in `<head>`
- No inline event handlers (no `onclick` attributes)

### 2. Modern JavaScript (ES6+)
- Use `const` and `let` (never `var`)
- Use arrow functions where appropriate
- Use template literals for string interpolation
- Use destructuring, spread operators, and modern array methods
- Use async/await for asynchronous operations

### 3. Code Organization
```javascript
// ==================
// Constants & Configuration
// ==================

// ==================
// Utility Functions
// ==================

// ==================
// Main Application Logic
// ==================

// ==================
// Event Listeners & Initialization
// ==================

// Initialize when DOM is ready
document.addEventListener('DOMContentLoaded', () => {
  // Initialization code
});
```

### 4. DOM Manipulation
- Wait for `DOMContentLoaded` before accessing DOM
- Cache DOM selections in variables
- Use `querySelector` and `querySelectorAll` over older methods
- Prefer event delegation for dynamic content
```javascript
// Good
const button = document.querySelector('.btn-submit');
button.addEventListener('click', handleClick);

// Event delegation
document.querySelector('.list').addEventListener('click', (e) => {
  if (e.target.matches('.list-item')) {
    // Handle click
  }
});
```

### 5. Error Handling
- Wrap risky operations in try-catch blocks
- Provide fallbacks for failed operations
- Console log errors for debugging (can be removed in production)
```javascript
try {
  // Risky operation
} catch (error) {
  console.error('Operation failed:', error);
  // Provide user feedback
}
```

### 6. Best Practices
- Avoid global variables (use IIFE or modules pattern)
- Use meaningful variable and function names
- Keep functions small and focused (single responsibility)
- Add comments for complex logic
- Validate user input
- Remove event listeners when no longer needed

---

## Validation & Compliance

### 1. Validation Checklist
Before considering an example complete:
- [ ] HTML validates at https://validator.w3.org/
- [ ] No console errors in browser
- [ ] Works in major browsers (Chrome, Firefox, Safari, Edge)
- [ ] Responsive on mobile, tablet, and desktop
- [ ] Keyboard navigation works completely
- [ ] Screen reader testing passes basic checks
- [ ] Color contrast meets WCAG AA standards
- [ ] All images have alt text
- [ ] Forms have proper labels and validation

### 2. Performance Considerations
- Minimize reflows and repaints
- Debounce or throttle frequent events (scroll, resize, input)
- Use CSS transforms for animations (better performance)
- Avoid layout thrashing in JavaScript

---

## Example Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="A brief description of this example">
  <title>Example Title - Descriptive Name</title>
  
  <style>
    /* ==================
       CSS Reset & Base
       ================== */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    :root {
      --primary-color: #007bff;
      --text-color: #333;
      --bg-color: #fff;
      --spacing: 16px;
    }
    
    body {
      font-family: system-ui, -apple-system, sans-serif;
      line-height: 1.6;
      color: var(--text-color);
      background-color: var(--bg-color);
      padding: var(--spacing);
    }
    
    /* ==================
       Layout
       ================== */
    
    /* ==================
       Components
       ================== */
    
    /* ==================
       Responsive
       ================== */
    @media (min-width: 768px) {
      /* Tablet+ styles */
    }
  </style>
</head>
<body>
  <header>
    <h1>Page Title</h1>
  </header>
  
  <main>
    <section>
      <h2>Section Heading</h2>
      <!-- Content -->
    </section>
  </main>
  
  <footer>
    <p>&copy; 2025 Example Page</p>
  </footer>
  
  <script>
    'use strict';
    
    // ==================
    // Constants
    // ==================
    
    // ==================
    // Functions
    // ==================
    
    // ==================
    // Initialization
    // ==================
    document.addEventListener('DOMContentLoaded', () => {
      console.log('Page loaded and ready');
    });
  </script>
</body>
</html>
```

---

## Common Patterns & Solutions

### 1. Accessible Modal/Dialog
```html
<div class="modal" role="dialog" aria-labelledby="modal-title" aria-modal="true" hidden>
  <div class="modal-content">
    <h2 id="modal-title">Modal Title</h2>
    <p>Modal content</p>
    <button class="modal-close" aria-label="Close modal">×</button>
  </div>
</div>
```

### 2. Accessible Tab Component
```html
<div class="tabs">
  <div role="tablist" aria-label="Content tabs">
    <button role="tab" aria-selected="true" aria-controls="panel-1" id="tab-1">Tab 1</button>
    <button role="tab" aria-selected="false" aria-controls="panel-2" id="tab-2">Tab 2</button>
  </div>
  <div role="tabpanel" id="panel-1" aria-labelledby="tab-1">Content 1</div>
  <div role="tabpanel" id="panel-2" aria-labelledby="tab-2" hidden>Content 2</div>
</div>
```

### 3. Form Validation Pattern
```javascript
const form = document.querySelector('form');
form.addEventListener('submit', (e) => {
  e.preventDefault();
  
  // Validate
  const formData = new FormData(form);
  const data = Object.fromEntries(formData);
  
  // Process
  console.log('Form data:', data);
});
```

### 4. Responsive Navigation
```html
<nav aria-label="Main navigation">
  <button class="nav-toggle" aria-expanded="false" aria-controls="nav-menu">
    <span class="sr-only">Toggle navigation</span>
    ☰
  </button>
  <ul id="nav-menu" class="nav-menu">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```

---

## Documentation Requirements

Each example file should include:
1. A comment block at the top describing the example
2. Comments explaining complex logic or patterns
3. A title that clearly describes the example's purpose
4. Clear section organization with comments

Example header comment:
```html
<!--
  Example: [Name]
  Description: [Brief description of what this example demonstrates]
  Features: [List of key features or patterns demonstrated]
  Date Created: [Date]
-->
```

---

## Quality Standards Summary

✅ **DO:**
- Use semantic HTML5 elements
- Ensure full keyboard accessibility
- Provide meaningful alt text for images
- Use modern CSS (Flexbox, Grid, custom properties)
- Write clean, commented JavaScript
- Follow mobile-first responsive design
- Validate HTML and check for console errors
- Test in multiple browsers and screen sizes

❌ **DON'T:**
- Use inline styles (except for dynamic JS-generated styles)
- Use inline event handlers (`onclick`, etc.)
- Skip accessibility features
- Use deprecated HTML elements
- Ignore semantic structure
- Create complex dependencies
- Skip responsive design considerations
- Leave console errors unresolved

---

## Version History
- v1.0 (2025-12-30): Initial creation of agentic instructions

