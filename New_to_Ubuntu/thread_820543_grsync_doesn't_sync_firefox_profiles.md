---
title: "grsync doesn't sync firefox profiles"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by naggis on 2008-06-06
I want to use the same firefox profile on my xp box and on my wireless networked Hardy laptop. Firefox -profilemanager will not allow me to use the desktop profile on the laptop. So I had this great idea to create a folder on the laptop and sync it with the xp box. 
I installed grsync and all went well with the first synchronisation even if it did take a long time. But now if there is a change to the profile on the xp box and I sync the two folders, the change is not shown on the laptop.
The change is shown if the xp folder is copied and pasted into the laptop folder so it is something that I am not doing in grsync.
Has anyone any ideas?
Thanks

---

### Post by rampageoberon on 2008-06-06
Why don't you try link the profiles. In that way you don't need to be running any other application to synchronise. But I'm not sure it will work if you are using both the XP and ubuntu firefox together.

You can try mirrordir too to copu the firefox profile and then change the Profile.ini file to point to the correct one.

Hope that helps

---

### Post by naggis on 2008-06-06
When you say "link the profiles" do you mean use just one folder containing one profile to use on both machines? If so, that is what I tried to do but profilemanager kept coming up with error messages telling me that I couldn't do it.
If you have a means of linking the two separate profiles, could you please give me a few more details as I cant think of a way.
I will also have a look at the program you suggest to copy/mirror the profiles.
Thanks for the input

---

