# ShopAssist AI — E-Commerce Customer Support Agent

An automated, intelligent customer support assistant built with **n8n**, **OpenAI GPT-4o**, and **Google Sheets**.

`ShopAssist AI` handles real-time customer inquiries by connecting an LLM-powered agent to live spreadsheet databases. It autonomously decides when to check inventory, fetch order statuses, or pull store policies based on user messages.

---

## 🌟 Key Features

- 📦 **Inventory & Product Lookup:** Checks live stock levels, prices, categories, and warranty durations.
- 🚚 **Order Status Tracking:** Fetches tracking numbers, delivery dates, and current fulfillment status using Order IDs.
- 📋 **Store FAQ & Policy Assistant:** Instant answers regarding returns, shipping rates, payment methods, and warranty claims.
- 💬 **Contextual Memory:** Retains conversation context across multiple messages for seamless multi-turn support.

---

## 🏗️ Architecture & Workflow


The AI Agent acts as the router, calling specific Google Sheet tools based on user intent:

- **Product_Catalog_Tool** → Queries product availability, pricing, and specs.
- **Order_Tracking_Tool** → Looks up order status, tracking IDs, and estimated delivery dates.
- **FAQ_Policy_Tool** → Fetches store rules, return windows, and shipping fees.

---

## 📁 Repository Structure

```text
n8n-ecommerce-support-agent/
│
├── README.md                      <-- Project documentation
├── .gitignore                     <-- Git ignore rules
├── ShopAssist_AI_Workflow.json    <-- Sanitized n8n workflow file
├── ShopAssist_Store_Data.csv         

```

---

## 🚀 Getting Started

### Prerequisites

- An active n8n instance (Cloud or Self-Hosted).
- An OpenAI API Key (configured with access to `gpt-4o`).
- A Google Account with access to Google Sheets.

### Step 1: Set Up Google Sheets Data

1. Create a new Google Spreadsheet named `ShopAssist_Store_Data`.
2. Add 3 tabs (worksheets) named:
   - `Product Catalog`
   - `Order Tracking`
   - `FAQ & Policy`
3. Import the provided `.csv` files (`product_catalog.csv`, `order_tracking.csv`, `faq_policy.csv`) into their respective tabs.

### Step 2: Import Workflow into n8n

1. Download `ShopAssist_AI_Workflow.json` from this repository.
2. In n8n, navigate to **Workflows > Import from File**.
3. Select `ShopAssist_AI_Workflow.json`.

### Step 3: Connect Credentials & Tools

1. Click the **OpenAI Chat Model** node and attach your OpenAI API Key.
2. Click each of the three **Google Sheets Tool** nodes:
   - Authenticate your Google OAuth2 / Service Account credentials.
   - Select your `ShopAssist_Store_Data` spreadsheet.
   - Map each tool node to its corresponding tab (`Product Catalog`, `Order Tracking`, `FAQ & Policy`).
3. Save and activate the workflow!

---

## 🧪 Test Queries (15 Examples)

You can test the agent directly in the n8n Chat Interface using these queries:

### 📦 Product & Inventory Inquiries

1. "Do you have the Ergonomic Mechanical Keyboard in stock right now?"
2. "How much does the Ultra-Wide 34-inch Gaming Monitor cost, and what is its warranty period?"
3. "Is the Magnetic Wireless Power Bank currently available?"
4. "Can you recommend any ergonomic home office items from your catalog?"
5. "How many Stainless Steel Water Bottles do you currently have in stock?"

### 🚚 Order Status & Tracking Inquiries

6. "Can you give me an update on my order ORD-1004?"
7. "Where is order ORD-1002 and when should I expect it to arrive?"
8. "What is the tracking number for order ORD-1009?"
9. "Why was my order ORD-1005 cancelled?"
10. "Has order ORD-1020 been shipped yet?"

### 📋 Store FAQ & Policy Inquiries

11. "How much money do I need to spend to qualify for free shipping?"
12. "What is your return policy window if I want to send back an item?"
13. "How do I submit a warranty claim if my device arrives broken?"
14. "How long does it take to get my money back after returning a product?"

### 🔄 Multi-Tool / Multi-Intent Query

15. "I recently placed order ORD-1003. Was it delivered, and how long do I have to return it if I don't like it?"
