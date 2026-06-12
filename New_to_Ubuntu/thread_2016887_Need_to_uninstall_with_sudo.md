---
title: "Need to uninstall with sudo ???"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by morhin on 2012-07-04
Fairly new, using 10.04 for now.

I was trying to set up bluetooth with my older Blackberry 8700.

I downloaded the packages from the Software Center with no results.

I found Ubuntu-Geek and followed the instructions which were to download the following using sudo....

"sudo add-apt-repository ppa:doctormo/barry-snapshot
sudo apt-get update
sudo apt-get install barry-util opensync-plugin-barry-4x"

I did that but nothing worked so I just decided to leave things alone. I removed the Software Center stuff but now I have a red triangle sign showing up that says I need to update my software. When I do it tells me this.....

                                   "Failed to fetch http://[ppa.launchpad.net/doctormo/barry-snapshot/ubuntu/dists/lucid/main/binary-i386/Packages.gz]("http://ppa.launchpad.net/doctormo/barry-snapshot/ubuntu/dists/lucid/main/binary-i386/Packages.gz")  404  Not Found  
 Some index files failed to download, they have been ignored, or old ones used instead."

I noted the "barry-snapshot" bit but don't know how to deal with it. Do I need to uninstall something? My updates are up to date except for this thing.
If I need to uninstall what do I need to type in?


Thanks
Morhin
I learn by encountering new things, messing them up, then fixing them. It's a round-a-bout method, but it works for me.

:-k

---

### Post by lrcaballero on 2012-07-04
Do you have synaptic install?

---

### Post by Paqman on 2012-07-04
Open up Software Sources and uncheck or delete that line on the "other software" tab.

---

### Post by morhin on 2012-07-05
*Do you have synaptic install? (Ircabellero)*
Don't understand that question. Being fairly new there's a lot I don't understand. I do appreciate your reply and your effort to help.



Paqman - that was a nice fix. Didn't even know that was there but I'll remember it now.


Bottom line..... the triangle didn't show up today. 


Now all I have to do is figure out how to mark this 'solved'.



Thanks
Morhin

I learn by encountering new things, messing them up, then fixing them. It's a round-a-bout method, but it works for me.
):P

---

