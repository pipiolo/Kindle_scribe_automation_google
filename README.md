# Kindle_scribe_automation_google
Automate kindle scribe emails download and archive in googledrive

📧 Automated Amazon PDF Downloader

Google Apps Script that automatically downloads PDF files from Amazon emails and saves them to Google Drive.

✨ Features

· 🔍 Smart Filtering: Only processes emails from do-not-reply@amazon.com
· 📁 Automatic Organization: Creates and uses "Notas KS" folder in Google Drive
· 🔄 PDF Detection: Identifies and downloads PDF links from Amazon, AWS, and S3
· 🎯 Smart Naming: Automatically extracts and cleans filenames
· 📅 Date Cleaning: Removes date patterns from filenames automatically
· 🚫 Duplicate Handling: Replaces existing files with same names
· 📧 Mark as Read: Automatically marks processed emails as read

🚀 How to Use

Prerequisites

· Google Account (Gmail + Google Drive)
· Access to Google Apps Script

Installation

1. Open Google Apps Script
   ```javascript
   // Go to: https://script.google.com
   // Create a new project
   ```
2. Copy the Code
   · Paste all provided code into the editor
3. Enable Advanced Services
   ```javascript
   // Go to Resources > Advanced Google Services
   // Enable:
   // - Google Drive API
   // - Gmail API
   ```
4. Set Up Triggers (Optional)
   ```javascript
   // Go to Edit > Current project's triggers
   // Add trigger for automatic execution
   ```

Execution

Manual Execution:

```javascript
// In Apps Script editor, run:
descargarAdjuntoAmazonPorRemitente()
```

Automatic Execution:

· Set up triggers for periodic execution (hourly, daily, etc.)

📁 Project Structure

Main Functions

Function Description
descargarAdjuntoAmazonPorRemitente() Main function that orchestrates the process
obtenerURLFinalPDF(url) Follows redirects to get the actual PDF URL
extraerNombreRealDesdeURL(urlFinal, urlOriginal) Extracts smart filenames from URLs
limpiarFechaDelNombre(nombreArchivo) Cleans date patterns from filenames
extraerNombreDeS3URL(url) Extracts specific names from S3 URLs

Target Folder Structure

```
Google Drive/
└── 📁 Notas KS/
    ├── 📄 amazon-invoice.pdf
    ├── 📄 electronics-purchase.pdf
    └── 📄 clothing-order.pdf
```

⚙️ Configuration

Email Search Query

```javascript
// Current search query:
'amazon AND is:unread'

// You can modify for other filters:
'amazon AND subject:invoice AND is:unread'
'amazon AND newer_than:7d'
```

Date Patterns Removed

The script automatically removes:

· 2025-09-24-15-41 → Becomes filename.pdf
· 2025-09-24 → Becomes filename.pdf
· 20250924-1541 → Becomes filename.pdf
· And other common formats...

📊 Logging and Monitoring

The script generates detailed logs:

```
✅ Valid sender detected: do-not-reply@amazon.com
=== PROCESSING URL ===
Original URL: https://amazon.com/link-to-pdf
Final PDF URL: https://s3.amazonaws.com/real-file.pdf
Original name: invoice-2025-09-24-15-41.pdf
Clean name: invoice.pdf
✅ DOWNLOADED to 'Notas KS': invoice.pdf
```

🛠 Troubleshooting

Common Issues

1. No Emails Found
   · Verify emails are in inbox
   · Confirm they're from do-not-reply@amazon.com
2. PDFs Not Downloading
   · Check logs for detected URLs
   · Verify Google Drive permissions
3. Incorrect Filenames
   · Script uses multiple extraction methods
   · Logs show the cleaning process

Required Permissions

· GmailApp: Read and mark emails
· DriveApp: Create folders and files
· UrlFetchApp: Download files from internet

🔒 Security

· Only processes emails from verified senders
· Does not store sensitive information
· Only accesses unread Amazon emails

📝 License

This project is open source and available under the MIT License.

🤝 Contributing

Contributions are welcome! Please:

1. Fork the project
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

⚠️ Disclaimer

This script is not affiliated with Amazon.com. It is an independent tool for automating document downloads.

---

Need help? Check logs in View > Logs in Apps Script for detailed diagnostics.
