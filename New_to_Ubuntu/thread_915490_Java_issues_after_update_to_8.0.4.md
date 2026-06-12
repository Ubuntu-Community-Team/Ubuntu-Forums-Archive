---
title: "Java issues after update to 8.0.4"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by tcobb on 2008-09-09
Hi All, I'd REALLY appreciate some help. I have to use an emulator run by java for my job. The other day I updated my system to 8.0.4. Now, when I open Firefox and try to login to my emulator it says Additional Plugins are required to view this page. So, I click on the download plugins. It says the following plugins are available: Java Runtime Environment. I press next to install and then it says Not Available. Then it gives the option for a manual install. I've tried this over and over to no avail. I would very much welcome any help with this. As I said I REALLY need this for my job.

---

### Post by aloshbennett on 2008-09-10
are you running 32 bit or 64 bit?
Cos sun-java plugins are available for 32 bit. You have to use iced-tea for 64 bits.

---

### Post by Seisen on 2008-09-10
Make sure that the multiverse repository is enabled. Go to System>Admistration>Software Sources to check.

---

### Post by tcobb on 2008-09-10
Where do I find out if it's 32 or 64 bit? 

Yes, multiverse is enabled.

---

### Post by Ptero-4 on 2008-09-10
type uname -m in a terminal window. It would tell i686 if you're on x86 and amd64 on x64.

---

### Post by Seisen on 2008-09-10
Alright try installing this package: sun-java6-plugin

That will install the java plugin for Firefox.

---

### Post by tcobb on 2008-09-10
I typed in the terminal and it came up i686. 

sun java 6 plugin is already installed.

---

