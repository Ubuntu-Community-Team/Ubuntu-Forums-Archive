---
title: "Gambas Printing Problem"
date: 2011-01-12
forum: Programming Talk
---

### Post by etdsbastar on 2011-01-12
Hello Users,

I am using Gambas 2.22 with gb.report component. I had successfully created the print, but the report is only taking A4 as the default size. If I am giving the custom size the print is coming on top-left side in a A4 size paper and if I am using custom size paper on the printer, it is printed only half. Below given is the code. PLEASE HELP. 

```
  Report.Clear
  Report.Size = "Custom"
  Report.Width = "10.5 cm"
  Report.Height = "15 cm"
  Report.LineStyle = Line.Solid
  Report.Padding = "0.15 cm"
  Report.Resolution = Desktop.Resolution
```

---

