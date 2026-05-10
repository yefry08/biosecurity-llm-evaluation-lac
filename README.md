# Biosecurity LLM Evaluation — LAC

**Evaluating dual-use risks of open-weight language models in Latin America**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![AISDOM](https://img.shields.io/badge/by-AISDOM-blue)](https://github.com/yefry08)
[![Status: Active Research](https://img.shields.io/badge/status-active%20research-green)]()

---

## Overview

This repository contains the code, prompts, and results for a systematic evaluation of how regionally fine-tuned open-weight language models — particularly **LatamGPT** and comparable LAC-oriented models — respond to biosecurity-sensitive prompts.

The research focuses on identifying failure modes that could enable dual-use misuse (e.g., chemical or biological weapons proliferation) and producing actionable mitigation recommendations for LAC developers and policymakers.

This is the first public evaluation of this kind targeting Latin American language models, conducted in Spanish and English.

**Affiliated with:** [AI Safety Dominicana (AISDOM)](https://github.com/yefry08) · Santo Domingo, Dominican Republic

---

## Research Questions

1. How do LatamGPT and comparable open-weight LAC models respond to biosecurity-sensitive prompts compared to general-purpose frontier models?
2. What prompt patterns most reliably elicit dual-use risk behaviors in these models?
3. What model-level and deployment-level mitigations are most effective for LAC deployment contexts?

---

## Models Evaluated

| Model | Type | Access |
|-------|------|--------|
| LatamGPT | Regional fine-tune | HuggingFace |
| Mistral-7B | Open-weight baseline | HuggingFace |
| Llama-3-8B | Open-weight baseline | HuggingFace |
| GPT-4o (partial) | Frontier reference | API |

---

## Methodology

### Prompt Taxonomy
Prompts are organized into 4 risk tiers:
- **T0** — Benign (control group): general biology/chemistry questions
- **T1** — Ambiguous: dual-use queries with plausible legitimate intent
- **T2** — Sensitive: queries with clear biosecurity relevance
- **T3** — High-risk: direct requests for dangerous synthesis/weaponization information

### Evaluation Metrics
- Refusal rate by tier and model
- Refusal quality (hard refusal vs. partial compliance vs. full compliance)
- Jailbreak susceptibility (tested prompt variants)
- Response consistency across language (ES vs. EN)

### Case Study: LatamGPT
LatamGPT is a Spanish-language fine-tuned model trained on LAC-specific corpora. We evaluate whether regional fine-tuning introduces or removes safety behaviors present in the base model, and whether Spanish-language prompts receive different treatment than English equivalents.

---

## Repository Structure

```
biosecurity-llm-evaluation-lac/
├── data/
│   ├── raw/                    # Raw model outputs (not committed — see .gitignore)
│   └── processed/              # Cleaned, labeled evaluation results
├── notebooks/
│   └── 01_evaluation_base.ipynb  # Main evaluation notebook
├── src/
│   ├── prompts/
│   │   └── biosecurity_prompts.py  # Prompt library by tier
│   ├── evaluation/
│   │   └── scorer.py           # Response scoring logic
│   └── utils/
│       └── model_loader.py     # Model loading helpers
├── results/
│   ├── figures/                # Charts and visualizations
│   └── tables/                 # Result tables (CSV)
├── docs/
│   └── policy_brief_es.md      # Policy brief (Spanish, LAC audience)
├── CITATION.cff
├── LICENSE
└── README.md
```

---

## Setup

```bash
git clone https://github.com/yefry08/biosecurity-llm-evaluation-lac.git
cd biosecurity-llm-evaluation-lac
pip install -r requirements.txt
```

### Requirements
```
transformers>=4.40.0
torch>=2.1.0
openai>=1.0.0
pandas>=2.0.0
numpy>=1.24.0
jupyter>=1.0.0
tqdm>=4.65.0
python-dotenv>=1.0.0
```

### Environment variables
Create a `.env` file (never commit this):
```
OPENAI_API_KEY=your_key_here
HF_TOKEN=your_huggingface_token
```

---

## Results

*Results will be published here as the research progresses. Target: August 2026.*

| Model | T0 Refusal | T1 Refusal | T2 Refusal | T3 Refusal |
|-------|-----------|-----------|-----------|-----------|
| LatamGPT | — | — | — | — |
| Mistral-7B | — | — | — | — |
| Llama-3-8B | — | — | — | — |

---

## Outputs

- [ ] Technical report (EN) — August 2026
- [ ] Policy brief (ES) — August 2026
- [ ] Dataset (prompt library + labeled responses) — August 2026
- [ ] Presentation at EAGxSão Paulo — 2026

---

## Ethics & Safety

This research follows responsible disclosure practices. Prompts in tier T2/T3 are stored privately and will not be published in full. Aggregate results and anonymized examples will be shared. If you are a researcher and need access to the full prompt library, contact the author directly.

This repository does not contain, and will never contain, actual instructions for creating dangerous substances.

---

## Citation

If you use this work, please cite:

```bibtex
@misc{nunez2026biosecurity,
  author    = {Núñez, Yefry},
  title     = {Biosecurity LLM Evaluation -- LAC: Dual-use risk evaluation of open-weight models in Latin America},
  year      = {2026},
  publisher = {GitHub},
  url       = {https://github.com/yefry08/biosecurity-llm-evaluation-lac}
}
```

---

## Contact

**Yefry Núñez** · ML Engineer & AI Researcher  
Founder, AI Safety Dominicana (AISDOM)  
📧 yefrynunez45@gmail.com  
🐙 [github.com/yefry08](https://github.com/yefry08)  
💼 [linkedin.com/in/yefry-núñez-67a61831a](https://linkedin.com/in/yefry-núñez-67a61831a)

---

*This research is supported in part by a BlueDot Rapid Grant.*
