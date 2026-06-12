---
title: "Xmlstarlet... again"
date: 2007-11-15
forum: Programming Talk
---

### Post by Dannik on 2007-11-15
Hey guys, I'm trying to validate a simple xml file with xmlstarlet.
Here's the xml
```

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE SCHEDULE SYSTEM "schedule.dtd">
<SCHEDULE WEEK="1">
 <SHOW SID="s1">
  <NAME>Name1</NAME>
  <TYPE>Type1</TYPE>
 </SHOW>
  <SHOW SID="s2">
  <NAME>Name2</NAME>
  <TYPE>Type2</TYPE>
 </SHOW>
  <SHOW SID="s3">
  <NAME>Name3</NAME>
  <TYPE>Type3</TYPE>
 </SHOW>
  <SHOW SID="s4">
  <NAME>Name4</NAME>
  <TYPE>Type4</TYPE>
 </SHOW>
</SCHEDULE>

```

here's DTD
```

<!ELEMENT SCHEDULE ANY>
<!ELEMENT SHOW ANY>
<!ELEMENT NAME ANY>
<!ELEMENT TYPE ANY>

<!ATTLIST SCHEDULE WEEK CDATA #REQUIRED>
<!ATTLIST SHOW SID ID #REQUIRED>

```

when I try to validate the file I get an error saying:  parser error : Content error in the external subset.

Please help.

---

