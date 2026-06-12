---
title: "Is there a way that will record the traffic every hour for everyday vnstat"
date: 2020-10-01
forum: New to Ubuntu
---

### Post by mmali on 2020-10-01
I am running vnstat on a teltonika (rut950) lte router for 6 days. I want to monitor the hourly traffic. When I export the database with vnstat --exportdb > vnstat_db I only get hourly records from last 24 hours, not for all 6 days. Is there a way that records all the hours for everyday and save it to the database?

---

### Post by ActionParsnip on 2020-10-01
You could setup a proxy server that logs requests. Is that what you mean? All the HTTP and HTTPS requests etc?

---

### Post by SeijiSensei on 2020-10-01
[https://oss.oetiker.ch/mrtg/](https://oss.oetiker.ch/mrtg/)

---

