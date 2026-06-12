---
title: "database input via web scraping"
date: 2014-12-06
forum: Programming Talk
---

### Post by unibroker on 2014-12-06
[COLOR=#000000][FONT=verdana]I am building a database of companies and the individual's contact info within those companies. I'm trying importxml and xpath as a way to scrape the associated websites as opposed to copying and pasting the information into a google spreadsheet. I do not care about continually updating the information as it rarely changes.  [/FONT][/COLOR][COLOR=#000000][FONT=verdana]I am trying to extract 7 pieces of information (company, contact, address....).[/FONT][/COLOR][COLOR=#000000][FONT=verdana] Am I correct in assuming that I have to come up with a unique importxml function for every website because their layouts may be different?  Is there a better way of importing this information?  Thanks in advance.[/FONT][/COLOR]

---

### Post by ofnuts on 2014-12-06
There are heuristics but unless you can latch on a small number of content identifiers or labels you will end up writing a function for each site, and this will be less efficient than cut and paste....

---

