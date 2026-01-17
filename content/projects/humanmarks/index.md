---
title: "HumanMark"
date: 2025-01-17
draft: false
description: "Open Source AI Content Detection - Privacy-First, Self-Hosted, Multi-Modal"
summary: "The only AI detector that runs 100% on your infrastructure. Detect AI-generated text, images, audio & video—offline, self-hosted, zero external API calls."
slug: "humanmark"
tags: ["AI", "Open Source", "Privacy", "Go", "Self-Hosted", "Content Moderation"]
categories: ["Projects"]
showTableOfContents: true
showHero: true
heroStyle: "background"
---

{{< lead >}}
**Your content. Your servers. Your control.** HumanMark is the open-source AI detection engine that never sends your data to the cloud.
{{< /lead >}}

{{< github repo="vinpatel/HumanMark" >}}

---

## 🤔 The Problem

Every AI detection service requires you to **upload your content to their servers**. That's a dealbreaker for:

{{< alert icon="shield-exclamation" cardColor="#fef2f2" iconColor="#dc2626" textColor="#7f1d1d" >}}
**Compliance Nightmare:** Healthcare (HIPAA), Legal (privilege), Finance (SOC2/PCI), and Government (classified) organizations **cannot** send sensitive data to third-party APIs.
{{< /alert >}}

**HumanMark runs entirely on YOUR infrastructure.** Your data never leaves your network. Period.

---

## ⚡ Quick Start

Get running in under 30 seconds:

{{< tabs tabTotal="3" >}}

{{< tab tabName="🐳 Docker" >}}
```bash
docker run -p 8080:8080 humanmark/humanmark
```
{{< /tab >}}

{{< tab tabName="📦 Go Install" >}}
```bash
go install github.com/vinpatel/humanmark/cmd/api@latest
humanmark
```
{{< /tab >}}

{{< tab tabName="🔧 Source" >}}
```bash
git clone https://github.com/vinpatel/humanmark.git
cd humanmark && make run
```
{{< /tab >}}

{{< /tabs >}}

Then detect AI content:

```bash
curl -X POST http://localhost:8080/verify \
  -H "Content-Type: application/json" \
  -d '{"text": "Your content here"}'
```

**Response:**
```json
{
  "id": "hm_abc123",
  "verdict": "human",
  "confidence": 0.87,
  "signals": {
    "sentence_variance": 0.42,
    "vocabulary_richness": 0.78,
    "contraction_ratio": 0.15
  }
}
```

---

## 🏆 Why HumanMark?

{{< chart >}}
type: 'radar',
data: {
  labels: ['Privacy', 'Speed', 'Accuracy', 'Cost', 'Multi-Modal', 'Self-Hosted'],
  datasets: [
    {
      label: 'HumanMark',
      data: [100, 95, 85, 100, 90, 100],
      backgroundColor: 'rgba(59, 130, 246, 0.2)',
      borderColor: 'rgb(59, 130, 246)',
      pointBackgroundColor: 'rgb(59, 130, 246)'
    },
    {
      label: 'Cloud Alternatives',
      data: [30, 60, 90, 20, 40, 0],
      backgroundColor: 'rgba(239, 68, 68, 0.2)',
      borderColor: 'rgb(239, 68, 68)',
      pointBackgroundColor: 'rgb(239, 68, 68)'
    }
  ]
}
{{< /chart >}}

### Feature Comparison

| Feature | HumanMark | GPTZero | Originality.ai | Turnitin |
|:--------|:--------:|:-------:|:--------------:|:--------:|
| **Self-Hosted** | ✅ | ❌ | ❌ | ❌ |
| **Works Offline** | ✅ | ❌ | ❌ | ❌ |
| **Open Source** | ✅ MIT | ❌ | ❌ | ❌ |
| **Zero Cost** | ✅ | ❌ | ❌ | ❌ |
| **Multi-Modal** | ✅ | ⚠️ | ⚠️ | ⚠️ |
| **API Limits** | ∞ | Tiered | Per-check | Per-seat |

---

## 🔬 How It Works

HumanMark uses **statistical forensics**—no ML models, no GPU required, instant results.

{{< tabs tabTotal="4" >}}

{{< tab tabName="📝 Text" >}}

| Signal | Human | AI |
|--------|-------|-----|
| Sentence length variance | High | Low |
| Vocabulary richness | Diverse | "Safe" words |
| Contractions | "don't", "I'm" | "do not", "I am" |
| Punctuation variety | !?;:— | Mostly periods |
| AI phrases | Rare | "As an AI..." |

{{< /tab >}}

{{< tab tabName="🖼️ Image" >}}

| Signal | Real Photo | AI Image |
|--------|-----------|----------|
| EXIF metadata | Present | Missing |
| Camera make | Apple, Canon | None |
| Sensor noise | Natural | Too clean |
| Compression | Consistent | Irregular |

{{< /tab >}}

{{< tab tabName="🎵 Audio" >}}

- File header analysis
- Encoder fingerprinting  
- AI tool markers (ElevenLabs, etc.)
- Temporal consistency checks

{{< /tab >}}

{{< tab tabName="🎬 Video" >}}

- Container metadata analysis
- Frame-by-frame consistency
- Generation tool signatures
- Encoding profile anomalies

{{< /tab >}}

{{< /tabs >}}

---

## 💼 Use Cases

{{< timeline >}}

{{< timelineItem icon="building-office" header="Enterprise Compliance" badge="HIPAA/GDPR" subheader="Healthcare, Finance, Legal" >}}
Organizations that cannot send data to third-party APIs. HumanMark runs on-premise—patient records, legal documents, and financial data never leave your network.
{{< /timelineItem >}}

{{< timelineItem icon="academic-cap" header="Education at Scale" badge="100K+ Students" subheader="Universities & Districts" >}}
Process millions of assignments without per-document fees. Self-hosted = unlimited usage at fixed infrastructure costs. Often 90%+ savings vs. commercial alternatives.
{{< /timelineItem >}}

{{< timelineItem icon="code-bracket" header="Developer Integration" badge="REST API" subheader="Content Platforms & Apps" >}}
Integrate AI detection into your product: content moderation, hiring tools, CMS plugins, browser extensions. Full REST API with SDKs coming soon.
{{< /timelineItem >}}

{{< timelineItem icon="shield-check" header="Government & Defense" badge="Air-Gapped" subheader="Classified Environments" >}}
Deploy in air-gapped networks with zero internet connectivity. Essential for classified environments, secure facilities, and critical infrastructure.
{{< /timelineItem >}}

{{< /timeline >}}

---

## 📊 Performance

Benchmarked on AWS c5.xlarge (4 vCPU, 8GB RAM):

{{< chart >}}
type: 'bar',
data: {
  labels: ['Requests/sec', 'Latency p50 (ms)', 'Latency p99 (ms)', 'Memory (MB)'],
  datasets: [{
    label: 'HumanMark',
    data: [12400, 8, 23, 45],
    backgroundColor: ['rgba(34, 197, 94, 0.8)', 'rgba(59, 130, 246, 0.8)', 'rgba(168, 85, 247, 0.8)', 'rgba(251, 146, 60, 0.8)']
  }]
},
options: {
  plugins: {
    title: {
      display: true,
      text: 'Performance Metrics'
    }
  },
  scales: {
    y: {
      beginAtZero: true
    }
  }
}
{{< /chart >}}

{{< badge >}}
12,400 req/sec
{{< /badge >}}

{{< badge >}}
8ms p50 latency
{{< /badge >}}

{{< badge >}}
45MB memory
{{< /badge >}}

{{< badge >}}
150ms cold start
{{< /badge >}}

---

## 🗺️ Roadmap

- [x] Text detection (statistical analysis)
- [x] Image detection (EXIF + forensics)
- [x] Audio detection (metadata)
- [x] Video detection (container analysis)
- [x] Docker support
- [x] Prometheus metrics
- [ ] 🔜 Browser extension
- [ ] 🔜 VS Code extension
- [ ] 🔜 WordPress plugin
- [ ] 🔜 Python & JavaScript SDKs
- [ ] 🔜 Admin dashboard

---

## 🔗 Links

{{< button href="https://github.com/vinpatel/HumanMark" target="_blank" >}}
⭐ Star on GitHub
{{< /button >}}

{{< button href="https://github.com/vinpatel/HumanMark/discussions" target="_blank" >}}
💬 Discussions
{{< /button >}}

---

## 📜 License

{{< alert "circle-info" >}}
**MIT License** — Use it however you want. Free forever. No premium tiers, no enterprise editions, no bait-and-switch.
{{< /alert >}}

---

*Built with ❤️ by [Vin Patel](https://vinpatel.com)*
