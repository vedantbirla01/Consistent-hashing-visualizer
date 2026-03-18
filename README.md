<div align="center">

<img src="client/pie-chart-svgrepo-com.svg" alt="Logo" width="80" height="80"/>

# Consistent Hashing Visualizer

*An interactive, full-stack visualization tool for understanding Consistent Hashing —*
*a core concept powering distributed systems, load balancers, and large-scale databases.*

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Visit-blue?style=for-the-badge)](https://consistent-hashing-visualizer-pi.vercel.app)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Overview

This project demonstrates **Consistent Hashing** — a distributed hashing algorithm used in production systems worldwide to ensure minimal data redistribution when servers are added or removed.

Built as a full-stack application with a **React frontend** and **Node.js/Express backend**, this tool allows users to interactively add/remove nodes and keys on a hash ring, observe real-time key redistribution, and understand the algorithm visually.

---

## 🔗 Live Demo

👉 [consistent-hashing-visualizer-pi.vercel.app](https://consistent-hashing-visualizer-pi.vercel.app)

---

## 🚀 Key Features

| Feature | Description |
|--------|-------------|
| ➕ Add / Remove Nodes | Dynamically add or remove server nodes on the hash ring |
| 🔑 Key Assignment | Add keys and watch them get assigned to the nearest clockwise node |
| 🔄 Auto Redistribution | Keys automatically reassign when topology changes |
| 📊 Hash Ring Visualization | SVG-based animated ring with real-time updates |
| 🗂️ Node-Key Mapping | Clear panel showing which keys belong to which node |
| 📋 Event Log | Real-time log of all system events with timestamps |

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| React 19 | UI framework |
| Vite | Build tool |
| Tailwind CSS v4 | Styling |
| Framer Motion | Animations |
| Axios | HTTP client |

### Backend
| Technology | Purpose |
|-----------|---------|
| Node.js | Runtime |
| Express.js | REST API framework |
| Node `crypto` | MD5 hashing |

---

## 📁 Project Structure
```
consistent-hashing-visualizer/
│
├── client/                        # React Frontend (Vite)
│   ├── src/
│   │   ├── components/
│   │   │   ├── HashRing.jsx       # SVG hash ring visualization
│   │   │   └── LogPanel.jsx       # Real-time event log
│   │   ├── App.jsx                # Root component & state management
│   │   └── main.jsx               # Entry point
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
│
└── server/                        # Node.js Backend (Express)
    ├── routes/
    │   └── ring.js                # Consistent hashing logic & API routes
    ├── index.js                   # Server entry point
    └── package.json
```

---

## 📖 How Consistent Hashing Works
```
Hash Ring (0 ─────────────────────────────── 2³²)

         Key3 ●                    ● Node A
                  \              /
                   \            /
         Node C ●   \          /   ● Key1
                     \        /
                      \      /
         Key2 ●        \    /        ● Node B
                        \  /
```

1. All **nodes and keys** are mapped onto a virtual ring using MD5 hashing
2. Each **key** is assigned to the **first node clockwise** from its position
3. When a **node is added** → only keys between it and its predecessor are redistributed
4. When a **node is removed** → only its keys move to the next node
5. This ensures **minimal disruption** across the entire system

---

## ⚙️ Run Locally

### Prerequisites
- Node.js v18+
- npm v9+

### 1. Clone the repository
```bash
git clone https://github.com/vedantbirla01/Consistent-hashing-visualizer.git
cd Consistent-hashing-visualizer
```

### 2. Start the backend
```bash
cd server
npm install
node index.js
# Server running on http://localhost:5000
```

### 3. Start the frontend
```bash
cd client
npm install
npm run dev
# Frontend running on http://localhost:5173
```

---

## 🌐 API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/ring/state` | Get current nodes and keys |
| `POST` | `/api/ring/add-node` | Add a new node `{ name }` |
| `POST` | `/api/ring/remove-node` | Remove a node `{ name }` |
| `POST` | `/api/ring/add-key` | Add a new key `{ key }` |
| `POST` | `/api/ring/reset` | Reset the entire ring |

---

## 💡 Real-World Applications

- **Distributed Caching** — Partitioning data across cache nodes with minimal reshuffling (Redis Cluster)
- **Load Balancing** — Routing requests to backend servers predictably with session stickiness
- **Database Sharding** — Distributing data across nodes in systems like Cassandra and DynamoDB
- **Message Queues** — Partitioning Kafka topics across brokers for high-throughput event streaming

---

## 🙋‍♂️ Author

**Vedant Birla**

[![GitHub](https://img.shields.io/badge/GitHub-vedantbirla01-black?style=flat&logo=github)](https://github.com/vedantbirla01)

---

<div align="center">
<i>Built with ❤️ to demonstrate distributed systems concepts through interactive visualization.</i>
</div>
