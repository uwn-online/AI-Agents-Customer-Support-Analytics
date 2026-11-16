
# Key DAX Measures

## 1. Total Tickets

```dax
Total Tickets =
COUNTROWS('Fact Support Tickets')
```

---

## 2. AI to Humans Tickets

```dax
AI to Humans Tickets =
CALCULATE(
    [Total Tickets],
    'Support Role'[Support Path] = "AI → human"
)
```
---

## 3. AI Resolution Rate

```dax
AI Resolution Rate =
DIVIDE(
    [AI Resolved Ticket],
    [AI Involved Tickets],
    0
)
```

---

## 4. AI Escalation Rate

```dax
AI Escalation Rate =
DIVIDE(
    [AI to Humans Tickets],
    [AI Only Tickets] + [AI to Humans Tickets],
    0
)
```
---

## 5. Total Repeat Cost

```dax
Total Repeat Cost =
SUM('Fact Support Tickets'[Repeat Cost EUR])
```

---

## 6. Total Support Cost

```dax
Total Support Cost =
[Total AI Cost] +
[Total Human Cost] +
[Total Repeat Cost]
```

**Supporting Measures**

```dax
Total AI Cost =
SUM('Fact Support Tickets'[AI Cost EUR])

Total Human Cost =
SUM('Fact Support Tickets'[Human Cost EUR])
```

---

## 7. Cost per Ticket

```dax
Cost per Ticket =
DIVIDE(
    [Total Support Cost],
    [Total Tickets],
    0
)
```

[Return to Project README](../README.md)
