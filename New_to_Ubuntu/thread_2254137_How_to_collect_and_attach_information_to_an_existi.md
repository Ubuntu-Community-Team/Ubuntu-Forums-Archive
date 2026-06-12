---
title: "How to collect and attach information to an existing bug report?"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by f(fanta) on 2014-11-25
I believe I have reproduced a bug that is filed already. What is the correct way to collect relevant information from my system, and attach it to the *existing* bug? The existing bug was filed by someone else.

I have tried following instructions provided by [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) but got an error:

[B]> apport-cli -f -p hud --save bug.apport

*** Collecting problem information

The collected information can be sent to the developers to improve the
application. This might take a few minutes.
......
> ubuntu-bug -c bug.apport -u 1390153
Usage: ubuntu-bug [options] [symptom|pid|package|program path|.apport/.crash file]

ubuntu-bug: error: -u/--update-bug option cannot be used together with options for a new report[/B]

Thank you for any advice.

---

### Post by carlwsnyder on 2014-11-25
Are you reporting a system crash, an application crash, or a non-crash related bug?  The answer to that question is important to knowing what information needs to be reported when adding information to an existing bug report.  Your report, especially with an automatically produced bug report, added to an existing bug report to which it may or may not be related, could be helpful or not at all helpful.

---

