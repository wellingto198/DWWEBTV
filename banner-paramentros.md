markdown
# Banner Component Documentation

## 📋 Global Parameters

| Parameter     | Type     | Required | Default    | Description                                                                 |
|---------------|----------|----------|------------|-----------------------------------------------------------------------------|
| `type`        | string   | No       | `"info"`   | Banner type (`info`, `warning`, `success`, `error`, `email`, `custom`)      |
| `dismissible` | boolean  | No       | `true`     | Allow users to close the banner                                            |
| `expiration`  | string   | No       | -          | Expiration date in `YYYY-MM-DD` format                                     |
| `priority`    | number   | No       | `1`        | Display priority (1-10)                                                   |

## 🎨 Content Parameters

```json
{
  "content": {
    "icon": "fa-envelope",
    "title": "Important Message",
    "messages": [
      "First paragraph",
      "Second paragraph"
    ]
  }
}
Parameter	Type	Description	Allowed Values Example
icon	string	Font Awesome icon class	"fa-regular fa-envelope"
title	string	Bold header text	Max 120 characters
messages	string[]	Main content paragraphs	Array of strings (1-3 items recommended)
🔗 Action Parameters
json
{
  "actions": [
    {
      "text": "Learn More",
      "url": "#",
      "type": "primary",
      "target": "_blank",
      "icon": "fa-external-link"
    }
  ]
}
Parameter	Type	Required	Default	Description
text	string	Yes	-	Button text
url	string	Yes	-	Action URL
type	string	No	"default"	Style type (default, primary, email)
target	string	No	"_self"	Link target
icon	string	No	-	Font Awesome icon
🎚️ CSS Custom Properties
css
:root {
  /* Base colors */
  --banner-info-color: #0066cc;
  --banner-warning-color: #ffcc00;
  --banner-success-color: #28a745;
  --banner-error-color: #dc3545;
  
  /* Dimensions */
  --banner-max-width: 1200px;
  --banner-border-width: 5px;
  
  /* Timing */
  --banner-transition-duration: 0.3s;
}
📌 Example Configurations
Basic Info Banner
json
{
  "type": "info",
  "content": {
    "title": "System Update",
    "messages": [
      "New features available!",
      "Please refresh your browser"
    ]
  }
}
Emergency Warning
json
{
  "type": "error",
  "dismissible": false,
  "expiration": "2024-12-31",
  "content": {
    "icon": "fa-triangle-exclamation",
    "title": "Critical Alert!",
    "messages": [
      "Security breach detected",
      "Immediate action required"
    ]
  },
  "actions": [
    {
      "text": "Secure Account",
      "url": "/security",
      "type": "primary",
      "icon": "fa-shield-halved"
    }
  ]
}
🚦 Validation Rules
Content Limits:

title: 120 characters max

messages: 3 items max

actions: 2 buttons max

Security:

URLs must start with https:// or relative paths (/path)

Disallowed URL schemes: javascript:, data:, file:

Performance:

Total banner size < 5KB

Images not allowed in content

💡 Best Practices
Use priority levels:

json
{
  "type": "warning",
  "priority": 9
}
Combine with expiration:

json
{
  "expiration": "2024-12-31",
  "content": {
    "title": "Holiday Special"
  }
}
Accessibility tips:

Use action type="primary" for main CTA

Include ARIA labels for icons

Maintain color contrast ratio ≥ 4.5:1

🔧 Troubleshooting
Issue	Solution
Banner not appearing	Check expiration date and priority levels
Buttons misaligned	Verify action array has ≤ 2 items
Icons not loading	Use full Font Awesome class names
Style inconsistencies	Check CSS variable overrides

This documentation provides a complete reference for implementing and customizing the banner component. Save as `BANNER_DOCS.md` for GitHub repositories.
