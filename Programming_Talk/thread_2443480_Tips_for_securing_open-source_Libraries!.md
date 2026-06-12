---
title: "Tips for securing open-source Libraries!"
date: 2020-05-16
forum: Programming Talk
---

### Post by mortalkorona on 2020-05-16
Hi,

I have no formal education in programming or have worked as a programmer in the past. But I have worked in a large international company with heavy emphasis on software R&D. So I have some sense of how things work in the developer industry.

Just decided to go all-in teaching myself how to code with **[COLOR=#daa520]Python3[/COLOR]** last year. In that journey I stumbled upon this great service for helping you keep track of **[COLOR=#daa520]security vulnerabilities[/COLOR]** while you are coding. By creating vulnerability reports for you every week based on your GitHub project repository. You can create these reports locally also.

This is great since most security vulnerabilities usually comes from **[COLOR=#daa520]library imports[/COLOR]** you create with Python3, which a hobby developer don't really have any control over. But with these Snyk reports it's just a matter of upgrading packages to the latest versions.

I don't work for Snyk or get any perks from them. _But I just wanted to share this useful gem to everyone who wants to harden their code game. It's free for hobby developers and cost a ton of money for Enterprises._

**Securing Open Source Libraries - Guy Podjarny & Liran Tal** - Aug 2019
[https://youtu.be/4_azpDngFyk](https://youtu.be/4_azpDngFyk)

**Automating remediation for vulnerabilities in Python dependencies using Snyk** - Feb 2020
[https://snyk.io/blog/automating-remediation-for-vulnerabilities-in-python-dependencies-using-snyk/](https://snyk.io/blog/automating-remediation-for-vulnerabilities-in-python-dependencies-using-snyk/)


**Which manifest files can be tested and monitored by Snyk?**
[https://support.snyk.io/hc/en-us/articles/360000911957-Language-support](https://support.snyk.io/hc/en-us/articles/360000911957-Language-support)

The Snyk monitoring service basically scans your pip **[COLOR=#daa520]requirements.txt[/COLOR]** file for library vulnerabilities.

---

