---
title: "how to give packages to friends"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-09-28
hi all,
i have hardy heron. I recently recommended my friend to switch to ubuntu hardy heron from windows. he did so and he is liking it so much. the problem is  .. he does not have internet connectionm but i have . he wants some packages which are not installed in ubuntu by default. i have all the packages he need.. installed in my pc. how do i give those packages to him ?

please help me by giving clear instructions.. thanks

---

### Post by ad_267 on 2008-09-28
If you browse to /var/cache/apt/archives you can copy the .deb files your friend needs from there. You have to make sure you get all the packages that are dependencies too, as you can't install a package unless you have first installed its dependencies. That is what makes it tricky to install packages without an internet connection.

---

### Post by bumanie on 2008-09-28
It may be possible to get some pre-packaged ones from [http://www.getdeb.net/](http://www.getdeb.net/) or try these two links [http://roshan18.wordpress.com/2007/05/30/ubuntu-without-internet-connection-or-full-package-cddvds/](http://roshan18.wordpress.com/2007/05/30/ubuntu-without-internet-connection-or-full-package-cddvds/) and [http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)
Could your friend bring his/her computer to your place and connect, to download what he/she needs?

---

### Post by terry_gardener on 2008-09-28
a way that you could do this is. 

create a folder in home directory for example repos

open synaptic and mark all the packages your friend needs. and then click file-generate package download script and save it in the repos folder. 

now open the terminal and navigate to the repos folder. 

for me it was "cd repos" and when in the folder type "./name you give to script" and it will download all the marked packages into this folder. 

now just burn the deb packages to disk or usb stick take it to your friends and install the packages.

hope this helps

---

### Post by spiderbatdad on 2008-09-28
You could try aptoncd. I haven't heard much mention of it for a while. [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by stalkingwolf on 2008-09-28
another option is, if you have the packages in question installed on your computer to install remastersys on your system and make a backup copy of your system then install from there.  You can also make a distributalbe copy.

---

### Post by luckydeveloper on 2008-09-28
> **terry_gardener said:**
> 
open synaptic and mark all the packages your friend needs. and then click file-generate package download script and save it in the repos folder. 



how and where can i find the menu/button to generate that script in synaptic. there is no option like that in synaptic...:(

---

### Post by luckydeveloper on 2008-09-28
> **spiderbatdad said:**
> You could try aptoncd. I haven't heard much mention of it for a while. [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

yeah i tried aptoncd ... i first created an aptoncd image(in hardy heron) and burnt it in a cd...

at that time, i had to format the system for some reason.. so when i installed ubuntu hardy...i tried that cd with my own system.. i restored the packages and it said that it has copied all the packages in var/cache directory. when i went to synaptic and tried to install same packages...it went on to download those packages newly from the servers(though the deb files are in var/cache).......

---

### Post by terry_gardener on 2008-09-29
luckydeveloper

the menu option to generate download script is in the menu at the top left hander corner called file. 

i have also attached the screenshot of it.

---

### Post by luckydeveloper on 2008-09-29
> **terry_gardener said:**
> luckydeveloper

the menu option to generate download script is in the menu at the top left hander corner called file. 

i have also attached the screenshot of it.


thank you so much.. that was so nice of you to send the screenshots.. i will try them and let you know

---

### Post by luckydeveloper on 2008-09-29
ok... now i have a cd full of deb files (packages my friend need).. how can he install them from the cd...

after inserting the cd in the drive... what can he do with it...

---

### Post by drs305 on 2008-09-29
> **luckydeveloper said:**
> ok... now i have a cd full of deb files (packages my friend need).. how can he install them from the cd...

after inserting the cd in the drive... what can he do with it...

With ubuntu installed on his computer, he can open synaptic. Go to Settings > Repositories > Third Party. Click on Add CD-ROM. It will ask you to insert a CD and it can be used as an installation source.

---

### Post by terry_gardener on 2008-09-30
he can either do what drs305 said which should be the easy option 

or when you insert the cd rom into the drive it will open automatically and you could just double the deb file that you want to install and click install package and it will install the package. 

synaptic way would be better for multiple deb file installs and double clicking might be better for single file/program installs.

atleast using the synaptic way he will get use to it for when he gets the internet and can access all the packages for himself.

---

