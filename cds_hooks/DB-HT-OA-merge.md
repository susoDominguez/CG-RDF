# <mark>`copd-assess`</mark>

| Metadata | Value
| ---- | ----
| specificationVersion | 1.0
| hookVersion | 2,0
| hookMaturity | [0 - Draft](../../specification/1.0/#hook-maturity-model)

## Workflow

<mark>The `DB-HT-OA-merge` hook is triggered when the practitioner is assessing the severity of the current patient's diabetes or hypertension or osteoarthritis.</mark>

## Context
<mark>The context contains information on the diagnosis of the patient with respect to the multimorbidity scenario.</mark>

Field | Optionality | Prefetch Token | Type | Description
----- | -------- | ---- | ---- | ----
<mark>`encounterId`</mark> | REQUIRED | No | *string* | <mark>identifier of current encounter</mark>
<mark>`patientId`</mark> | REQUIRED | No | *string* | <mark>identifier of current patient</mark>
<mark>`diabetes`</mark> | OPTIONAL | No | *object* | <mark>FHIR Condition resource with the latest diabetes diagnoses, if existing.</mark>
<mark>`hypertension`</mark> | OPTIONAL | No | *object* | <mark>FHIR Condition resource with the latest hypertension diagnoses, if existing.</mark>
<mark>`osteoarthritis`</mark> | OPTIONAL | No | *object* | <mark>FHIR Condition resource with the latest osteoarthritis diagnosis, if existing.</mark>

### Example


```json
{
  "hookInstance": "d1577c69-dfbe-44ad-ba6d-3e05e953b2ea", 
  "hook": "careplan-select",
  "context": {
    "encounterId": "285064-0", 
    "patientId": "1677163",
    "diabetes": {
          "resource": {
            "resourceType": "Condition",
            "id": "db",
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "46635009",
                  "display": "Diabetes mellitus type 1"
                }
              ]
            },
            "subject": {
              "reference": "Patient/1677163"
            }
          }
    },
        "hypertension": {
          "resource": {
            "resourceType": "Condition",
            "id": "ht",
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "38341003",
                  "display": "Hypertensive disorder, systemic arterial"
                }
              ]
            },
            "subject": {
              "reference": "Patient/1677163"
            }
          }
    },
    "osteoarthritis" : {
        "resource": {
            "resourceType": "Condition",
            "id": "oa",
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "396275006",
                  "display": "Osteoarthritis"
                }
              ]
            },
            "subject": {
              "reference": "Patient/1677163"
            }
          }
    }
  }
}



```

## Change Log

Version | Description
---- | ----
1.0 | FHIR resource parameters
