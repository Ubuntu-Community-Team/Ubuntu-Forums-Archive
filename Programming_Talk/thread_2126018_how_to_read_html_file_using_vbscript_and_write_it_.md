---
title: "how to read html file using vbscript and write it into an excel"
date: 2013-03-15
forum: Programming Talk
---

### Post by sravs448 on 2013-03-15
Hi,
I want read a html and write few columns from it into an excel table.
I am currently using a macro to do it. But need it in VBScript

Below given is the sample html.
I want to count the number of fail occurrences for complainace check and oracle table and write it into an excel.

_**HTML File:**_

[TABLE="width: 100%"]
[TR]
[TH="width: 10%"]Result[/TH]
[TH="width: 70%"]Detail[/TH]
[TH="width: 20%"]Time[/TH]
[/TR]
[TR]
[TD]INFO[/TD]
[TD] TEST STARTED
[/TD]
[TD]2/9/2012 4:53:30 AM[/TD]
[/TR]
[TR]
[TD]DONE[/TD]
[TD]Passed -he webservice call.[/TD]
[TD]2/9/2012 4:53:34 AM[/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]FAIL
[/COLOR][/TD]
[TD][COLOR=#ff0000]Failed on compliance check,[/COLOR][/TD]
[TD][COLOR=#ff0000]2/9/2012 4:55:22 AM[/COLOR][/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:33 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:36 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:37 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.
[/TD]
[TD]2/9/2012 4:55:38 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:39 AM[/TD]
[/TR]
[TR]
[TD]DONE[/TD]
[TD]Passed - the trade was found in the SybaseFund table.[/TD]
[TD]2/9/2012 4:55:42 AM[/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]FAIL
[/COLOR][/TD]
[TD][COLOR=#ff0000]Failed -  not found in the Oracletable.[/COLOR][/TD]
[TD][COLOR=#ff0000]2/9/2012 4:55:42 AM[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]FAIL
[/COLOR][/TD]
[TD][COLOR=#ff0000]Failed - not found in the Oracle table.[/COLOR][/TD]
[/TR]
[/TABLE]



_**Desired Result in Excel:**_


[TABLE="width: 372"]
[TR]
[TD][/TD]
[TD]ComplianceCheck[/TD]
[TD]Oracle[/TD]
[/TR]
[TR]
[TD="align: right"]2/9/2012      [/TD]
[TD]          1[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD="align: right"]2/3/2013[/TD]
[TD]           0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


[TABLE="width: 372"]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]




[TABLE]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by sravs448 on 2013-03-15
Hi,
I want read a html and write few columns from it into an excel table.
I am currently using a macro to do it. But need it in VBScript

Below given is the sample html.
I want to count the number of fail occurrences for complainace check and oracle table and write it into an excel.

_**HTML File:**_

[TABLE="width: 100%"]
[TR]
[TH]Result[/TH]
[TH="width: 70%"]Detail[/TH]
[TH="width: 20%"]Time[/TH]
[/TR]
[TR]
[TD]INFO[/TD]
[TD] TEST STARTED[/TD]
[TD]2/9/2012 4:53:30 AM[/TD]
[/TR]
[TR]
[TD]DONE[/TD]
[TD]Passed -he webservice call.[/TD]
[TD]2/9/2012 4:53:34 AM[/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]FAIL
[/COLOR][/TD]
[TD][COLOR=#ff0000]Failed on compliance check,[/COLOR][/TD]
[TD][COLOR=#ff0000]2/9/2012 4:55:22 AM[/COLOR][/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:33 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:36 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:37 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:38 AM[/TD]
[/TR]
[TR]
[TD]WARNING[/TD]
[TD]Error querying QA-ORA.[/TD]
[TD]2/9/2012 4:55:39 AM[/TD]
[/TR]
[TR]
[TD]DONE[/TD]
[TD]Passed - the trade was found in the SybaseFund table.[/TD]
[TD]2/9/2012 4:55:42 AM[/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]FAIL
[/COLOR][/TD]
[TD][COLOR=#ff0000]Failed -  not found in the Oracletable.[/COLOR][/TD]
[TD][COLOR=#ff0000]2/9/2012 4:55:42 AM[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#ff0000]FAIL
[/COLOR][/TD]
[TD][COLOR=#ff0000]Failed - not found in the Oracle table.[/COLOR][/TD]
[/TR]
[/TABLE]



_**Desired Result in Excel:**_


[TABLE="width: 372"]
[TR]
[TD][/TD]
[TD]ComplianceCheck[/TD]
[TD]Oracle[/TD]
[/TR]
[TR]
[TD="align: right"]2/9/2012[/TD]
[TD]          1[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD="align: right"]2/3/2013[/TD]
[TD]           0[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


[TABLE="width: 372"]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]




[TABLE]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by DuckHook on 2013-03-15
I don't mean to be unfriendly, but why on earth are you posting in a Linux forum? Wouldn't a Windows forum better suit your needs?

---

### Post by trent.josephsen on 2013-03-15
I have done stuff like this in Perl, but have no VBScript experience (and plan to keep it that way). You may wish to ask at Daniweb or Stack Overflow, where you'd be likely to find more VBScript experience than here at UF.

That said, if you post the code you're working on it's still possible someone here can help you fix it. You do have some code, right?

---

### Post by Sef on 2013-03-15
Merged threads. Please do not cross post. Thank you.

---

### Post by ofnuts on 2013-03-16
> **trent.josephsen said:**
> You do have some code, right?

*cough*

---

