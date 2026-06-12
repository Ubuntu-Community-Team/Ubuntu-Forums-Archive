---
title: "my subreport using jasperReport got blank"
date: 2009-08-04
forum: Programming Talk
---

### Post by sthiranga on 2009-08-04
I have my report, and my sub report
both are successfully compiled using ireport,but when I run it using java my
  sub report is n't shown!...Only master report shown.

my sub report sql is 
> Select * from Item where Item_N0=$P{Ino}when i change this query to 
> Select * from Item where Item_N0='I001'this.It run and shown the sub report.

I've create the map and put parameters too.
> Map params=new HashMap();
       params.put("Ino",I001);
Can anyone help me.

---

