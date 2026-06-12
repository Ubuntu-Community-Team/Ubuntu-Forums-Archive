---
title: "Setting OpenOffice.org2 documents default language (6.06)"
date: 2006-09-28
forum: Outdated Tutorials &amp; Tips
---

### Post by simohell on 2006-09-28
In Dapper it is not possible to set the default language for OpenOffice2.org in the way OpenOffice normally does it. You can change the default by changing the Ubuntu default setting "System -> Administration -> Language Support". This however changes language for the whole user interface.

To set the default language for OpenOffice.org2 not changing the UI language you need to create a template:

1. Change the language for the current document

Tools -> Options -> Language Settings -> Languages -> Default languages for documents

2. Save it as a template (.odt) (best place is ~/.openoffice.org2/user/template)

3. Go to File -> Templates -> Organise

4. Choose your template from "My Templates" (the folder .../user/template) an choose Command -> Set As Default Tempalte

5. Do the same thing with a spreadsheet template (.ods) with the desired language

---

