# 🔐 Sam Web Design Agency License Management API

![API Version](https://img.shields.io/badge/API-v1.0-blue.svg)

## 🚀 Overview

Welcome to **Samwda License Management API** — a **professional**, **scalable**, and **secure** API-driven application designed to streamline software license management for vendors and developers alike.

With SLM API, you get a **full-featured RESTful API** that empowers your applications to:

- ✅ Check license validity instantly  
- 🔓 Activate licenses seamlessly  
- 🔒 Deactivate licenses securely  

Built with **best practices** in mind, License Manager guarantees **robust data integrity**, **industry-grade security**, and **easy integration** — whether you’re a small startup or an enterprise.

> “Managing licenses has never been easier or more secure.”  

---

## ✨ Features

| Feature                         | Description                                                                                     |
|--------------------------------|-------------------------------------------------------------------------------------------------|
| 📡 **RESTful API**              | Clear, consistent, and easy-to-use endpoints for all license operations                          |
| 🔄 **Activation & Deactivation** | Smooth workflows to activate and deactivate licenses tied to devices or users                   |
| ⏱️ **Real-time Status**          | Immediate license status checks with detailed metadata                                          |
| 🔑 **Token-based Auth**          | Secure API token authentication required for activate and deactivate requests                   |
| 🔒 **HTTPS & Validation**        | Enforced HTTPS communication and rigorous input validation to protect against attacks          |
| 📚 **Comprehensive Docs**        | Full documentation with examples to guide integration                                          |

---

## 📖 API Documentation

### 🔐 Authentication

- API token **is required only** for **activate** and **deactivate** endpoints.
- No token is required to check license status.
- When needed, include a valid API token in the `api_token` parameter or `Authorization` header.

---

### 🛠️ Endpoints

Base URL: `https://samwda.ir/api/`

---

#### 1. 🔍 Check License Status

- **Endpoint:** `GET https://samwda.ir/api/?action=check`
- **Description:** Verify the current status of a license key.
- **Parameters:**

| Parameter     | Type   | Required | Description                       |
|---------------|--------|----------|---------------------------------|
| `key`         | string | Yes      | The license key to verify        |
| `site_url`    | string | Optional | The URL of the site using license (for logging) |
| `product_type`| string | Optional | The product type to check license against |

- **Response Example:**

```json
{
  "success": true,
  "valid": true,
  "license": "TEST-123-ABC",
  "expires_at": null,
  "product_type": "TEST",
  "signature": "SAM Web Design Agency Licensed API Response!"
}
```

- **Example Request:**

```bash
curl -X GET "https://samwda.ir/api/?action=check&key=ABC123-XYZ789&site_url=https%3A%2F%2Fexample.com&product_type=TEST"
```

---

#### 2. ✅ Activate License

- **Endpoint:** `POST https://samwda.ir/api/?action=activate`
- **Description:** Activate a license for a specific device or user.
- **Required Parameters (JSON body):**

```json
{
  "license_key": "ABC123-XYZ789",
  "site_url": "https://samwda.ir/",
  "api_token": "YOUR_API_TOKEN"
}
```

- **Response Example:**

```json
{
  "success": true,
  "message": "License activated successfully.",
  "activation_id": "act-456"
}
```

- **Example Request:**

```bash
curl -X POST "https://samwda.ir/api/?action=activate" \
  -H "Content-Type: application/json" \
  -d '{"license_key":"ABC123-XYZ789","device_id":"device-001","user_id":"user-123","api_token":"YOUR_API_TOKEN"}'
```

---

#### 3. ❌ Deactivate License

- **Endpoint:** `POST https://samwda.ir/api/?action=deactivate`
- **Description:** Deactivate an active license on a device or user.
- **Required Parameters (JSON body):**

```json
{
  "activation_id": "act-456",
 "api_token": "YOUR_API_TOKEN"
}
```

- **Response Example:**

```json
{
  "success": true,
  "message": "License deactivated successfully."
}
```

- **Example Request:**

```bash
curl -X POST "https://samwda.ir/api/?action=deactivate" \
  -H "Content-Type: application/json" \
  -d '{"activation_id":"act-456","api_token":"YOUR_API_TOKEN"}'
```

---

## 🫆 Security

Security is at the core of License Manager:

- **API Tokens:**  
  - Required only for activate and deactivate endpoints.  
  - Tokens should be stored securely and rotated regularly.  
  - Follow the principle of least privilege when assigning scopes.

- **HTTPS Enforcement:**  
  - All communication is mandatory over HTTPS to protect data in transit.

- **Input Validation:**  
  - Every input is validated and sanitized to prevent injection and other attacks.

- **Best Practices:**  
  - Secure storage of license keys and tokens.  
  - Regular security audits and updates.

---

## 🔐 Samwda License Check Form

This is a **graphical license check form**. Enter your license key and optionally a site URL to see if the license is active. The response is displayed in a clean visual format with signature verification.

**How to use:**
1. Enter your license key in the "License Key" field.
2. Optionally enter a site URL to check if the license is active on that site.
3. Click "Check License".
4. The form will show:
   - License status (Active / Inactive)
   - Expiration date (or Unlimited)
   - Site activation status (if URL provided)

**Address:**  
`https://samwda.ir/api/check/`

---

## 📚 Persian Documentation

For a Persian version of this documentation, please see [README.fa.md](README.fa.md).

---

## 💡 Need Help?

If you have questions or need assistance, please open an issue or reach out to the maintainers.

---

Thank you for using **Samwda License Management API**! 🎉

*Manage your licenses with confidence and ease.*
