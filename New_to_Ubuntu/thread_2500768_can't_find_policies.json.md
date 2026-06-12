---
title: "can't find policies.json"
date: 2024-09-11
forum: New to Ubuntu
---

### Post by cemenc2 on 2024-09-11
Hi all,

I have ubuntu LTS 24.04 and firefox v130 on a vmware virtual box.
plan is to get rid of welcome page for new users opening firefox and make couple more settings change (like home page etc.)

I have been searching for policies.json file and I can't find it on the hdd. I let "Files" app search the whole hdd and it couldn't find it.

if you know where are the settings for whole computer (all users) , I would appreciate if you could share it with me (I mean the location)

Thank you very much in advance.

---

### Post by TheFu on 2024-09-11
policies.json doesn't exist anywhere on my systems.   It is common for config files not to exist, unless they are necessary for a specific system.  That means you should create it in the documented location if you want to use it.  

[https://support.mozilla.org/en-US/kb/customizing-firefox-using-policiesjson](https://support.mozilla.org/en-US/kb/customizing-firefox-using-policiesjson)
> On Linux, the file goes into firefox/distribution, where firefox is the installation directory for Firefox, which varies by distribution - or you can specify system-wide policy by placing the file in /etc/firefox/policies. 

---

### Post by cemenc2 on 2024-09-11
I cannot find neither of those locations (folders).

---

### Post by TheFu on 2024-09-11
> **cemenc2 said:**
> I cannot find neither of those locations (folders).

Then you should create them.  Thought I was pretty clear about that.  This is normal for Unix-like OSes.  If you need a file or a directory and it doesn't exist, then make it yourself.

---

### Post by cemenc2 on 2024-09-11
TheFu, you are right to be short tempered. 
I didn't didn't see the paragraph above your first reply. 

thanks

---

### Post by TheFu on 2024-09-11
I didn't intend to come across as unhappy.  My concern was that I wasn't clear.  Nothing more.

---

### Post by grahammechanical on 2024-09-11
I have found this on the internet:

> To see what policies you have active on a computer, **type in about:policies in the address bar**. This will show a list of policies, including the policy name and value.13 Feb 2019




Do that and click on Documentation and look down the list until you see Homepage = Set and optionally lock the homepage. Click the link and see what that can do.

Regards

---

