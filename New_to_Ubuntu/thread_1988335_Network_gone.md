---
title: "Network gone"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Huzudra on 2012-05-27
So I have the dardnest problem.I was trying to browse the shared drives on another computer here (running win7 64bit) from my laptop (xubuntu 11.1) and it was giving me an error like "failed to open owner-pc". I forget the exact message, but I rebooted the win7 machine, that didn't fix it. So I restarted the laptop and now in file manager there is no network. I had it before. Now I do not. 


:confused: What and how did I break something by restarting? I just ran updates and restarted again, it's not there. On a whim I went to software center and searched Samba, it was not installed which seemed confusing since I thought to browse a windows workgroup/network you needed it. So I installed it, but not really sure what to do after that since I just had 'network' as an option from the file manager. Just double click and there's my shared computers and drives. But it's suddenly gone. Honestly, I haven't been monkeying with anything.

---

### Post by Huzudra on 2012-05-27
Now I open file manager again to go get a video to watch and kapow, network appears again, but I can't see anything on the network. Just has 'windows network' which clicks to open 'WORKGROUP' which is not accessible. I've had this 'not accessible' problem pop up once or twice before and rebooting computers then waiting a few minutes fixed it, but I NEVER had 'network' vanish from file manager.

---

### Post by Huzudra on 2012-05-27
Ok, now I can see one of the two other PC's on the network but I'm unable to access it. I click and after a long hang I get 'failed to open owner-pc failed to retrieve share list from server'.  

Both windows PC's can see each other and share back and forth, this laptop can only see one of the two pc's and cannot share/access. I even setup a samba share of the home directory of the laptop, and I cannot access it from the laptop (it can't browse itself). I get the same error but just a different computer name. 


After a few more minutes, the second PC is showing up, but also still unable to browse. Is there a way to force it to 'refresh' when this happens rather than waiting?:confused:

---

### Post by Huzudra on 2012-05-27
Came upon a link that I had read before and done before, did all the things it said again and now it all works again. I installed winbind (which I had done before but it wasn't installed now?) and did the steps here

[http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)

But I'm still very confused as to how this broke in the first place. The last thing I did to the system was to disable compositing (turned off effects like shadows). I've rebooted since then. All the sudden I can't browse the network shares, I restart, and 'network' is just gone, Samba is no longer installed nor is winbind. All the changes I had made to the conf files mentioned in the link were still there though. So confused! It works now.

---

