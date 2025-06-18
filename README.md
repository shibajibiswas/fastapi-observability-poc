
# 📊 Real-Time Monitoring of a FastAPI Data Pipeline using Prometheus and Grafana

> ✅ **Project Type**: Technical PoC  
> 🧱 **Stack**: FastAPI · Prometheus · Grafana · Python · Metrics/Monitoring  
> 🧠 **Author**: [Shibaji Biswas](https://www.linkedin.com/in/shibajibiswas) · TOGAF | PMP | Data & Architecture Strategist

## 🚀 Overview

This proof-of-concept demonstrates how to monitor a **dummy data ingestion pipeline** built with FastAPI, using Prometheus for metrics collection and Grafana for live visualization.  
It simulates a real-world architecture used in **citizen-facing public systems**, where performance monitoring, error detection, and latency tracking are critical.

## 🎯 Objectives

| Goal # | Description |
|--------|-------------|
| 1️⃣ | Expose application-level metrics (requests, errors, latency) |
| 2️⃣ | Enable Prometheus to scrape metrics from FastAPI’s `/metrics` endpoint |
| 3️⃣ | Visualize key metrics in Grafana dashboards |
| 4️⃣ | Simulate realistic user traffic using Locust |

## 🛠 Architecture Diagram (ASCII Style)

```
[ Locust Users ] 
       |
       v
 [ FastAPI App ]
       |
  +--> /metrics --> [Prometheus] --> [Grafana Dashboards]
       |
  +--> Background Task (simulates processing, latency, error)
```

## 🧱 Tech Stack

| Component               | Purpose                                           |
|------------------------|---------------------------------------------------|
| **FastAPI**            | API service with `/submit_data` endpoint         |
| **Prometheus**         | Metrics collection (requests, errors, latency)   |
| **Grafana**            | Visualization dashboard                          |
| **Locust**             | Load generation (simulates users)                |
| **prometheus_client**  | Python package for exposing custom metrics       |

## 📦 Features Implemented

| Feature | Description |
|---------|-------------|
| ✅ Metrics | Custom Prometheus metrics: requests, errors, latency |
| 🔁 Background Tasks | Simulates async processing with random delay |
| ⚠️ Error Simulation | Random 10% failure rate for realism |
| 🧪 Load Testing | Locust-based traffic with varied payload |
| 📊 Grafana Dashboard | Tracks total requests, error rate, avg latency |

## 📁 Project Structure

| File | Description |
|------|-------------|
| `main.py` | FastAPI app with background task |
| `metrics.py` | Prometheus metric definitions |
| `requirements.txt` | Python dependencies |
| `locustfile.py` | Load testing script |
| `prometheus.yml` | Prometheus scrape config |
| `README.md` | This documentation |

## 🧪 API Details

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/submit_data` | Accepts citizen info JSON, triggers background processing |

### Sample JSON Payload:
```json
{
  "name": "Ravi",
  "age": 32,
  "city": "Delhi"
}
```

## ⚙️ How to Run Locally

| Step | Command / Description |
|------|------------------------|
| 1️⃣ | `pip install -r requirements.txt` |
| 2️⃣ | `uvicorn main:app --reload` — Start FastAPI |
| 3️⃣ | `prometheus --config.file=prometheus.yml` — Start Prometheus |
| 4️⃣ | Open Prometheus UI → http://localhost:9090 |
| 5️⃣ | Open Grafana UI → http://localhost:3000 |
| 6️⃣ | `locust -f locustfile.py --host=http://localhost:8000` |
|     | → Visit `http://localhost:8089` to start load testing |

## 📊 Grafana Query Examples

| Purpose | PromQL Query |
|---------|--------------|
| Requests per second | `rate(app_requests_total[1m])` |
| Error rate | `rate(app_errors_total[1m])` |
| Avg processing time | `rate(app_processing_seconds_sum[1m]) / rate(app_processing_seconds_count[1m])` |

## 📘 Relevance to Real-World Use Cases

| Sector | Applicability |
|--------|---------------|
| 🌐 Public Sector | 24×7 citizen-facing services |
| 🧩 DPI/GovTech | Metrics + observability for IndiaStack/DPI projects |
| 🧠 Architects | Scalable, secure design for system observability |
| 🔍 DevOps | Telemetry, alerting, and real-time tracing foundation |

## 📎 Future Enhancements

| Feature | Description |
|---------|-------------|
| 🧠 Tracing | Integrate OpenTelemetry for end-to-end tracing |
| 🚨 Alerts | Add Prometheus alert rules + Grafana notifications |
| 🐳 Dockerize | Use Docker Compose for full local stack |
| ☁️ Cloud Deploy | Run in GCP or Azure with external monitoring |

## 🙌 Credits

Created by **Shibaji Biswas**  
🎓 TOGAF | PMP | Data Architect | Author of *Blockchain in Telecom*  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/shibajibiswas)
