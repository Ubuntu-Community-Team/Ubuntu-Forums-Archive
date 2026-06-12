---
title: "Damn Small .bin issue"
date: 2008-12-20
forum: Other OS Talk
---

### Post by linuxguymarshall on 2008-12-20
I am trying to run HLDS.bin (Half Life / Counter Strike server) in Damn Small linux but the terminal keeps telling me that that file does not exist even though the 'dir' command shows it.

---

### Post by jerome1232 on 2008-12-20
Remember linux is case sensitive, also once I've had this type of issue where it was actually a message from the executable itself (complaining about a dependency I didn't have)

So if you have the case right and you can see the file in your current working directory with ls then perhaps check and ensure you have the required libraries.

---

### Post by jrusso2 on 2008-12-20
You might need to be in the directory to start it and the thing about it being case sensitive is important also

---

### Post by linuxguymarshall on 2008-12-20
Ok I figured it out, the case was right but I had some file confusion because DSL dowloads files in places other than the home dir which I am not used to. 

But this brought up another problem. When you run the .bin it asks you to accept the EULA which I did however it did not give me the steam and readme files as it should have. Any ideas?

---

### Post by jerome1232 on 2008-12-20
You know I installed this once and it was a bit confusing, there is a readme that comes with it do you have that? Might even have a html help document.

I recall it not using steam, you just had this file that you can run and tell it which game server to download ./hldedicate deathmatch or something (it's been like 5 months so that command is nowhere near accurate, but it's something like that)

---

