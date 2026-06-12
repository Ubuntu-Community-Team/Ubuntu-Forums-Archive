---
title: "mv command"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by Toni_Vines on 2014-05-06
I'm trying to add some new aircraft into my installation of Flightgear. I have downloaded two zip files into my /Home/Downloads directory. I now need to move them to my /usr/share/games/flightgear/Aircraft directory and then unpack them. I have started with sudo -i to give me root permission but no matter how I try I keep being told that folder 'Spitfire' does not exist! 
Please help, I'm close to tearing my hair out!!
Thanking you.
Toni.

---

### Post by deadflowr on 2014-05-06
When you invoke sudo -i, you get put in root's home directory.
/root

So you will need to either move (cd) in your home folder or mv with the full path
mv /home/you/folder /place-it-goes/folder

---

### Post by papibe on 2014-05-06
Hi Toni_Vines.

'sudo -i' changes your current directory, so I think that's why you can't find the directory (besides I wouldn't recommend it since you will be doing all commands as root)/

I'd recommend adding the mv command to the sudo. For instance, if you are at your home directory
```
sudo mv -v ~/Downloads/Spitfire/ /usr/share/games/flightgear/Aircraft/
```
or moving to the Downloads directory:
```
cd Downloads

sudo mv -v Spitfire/ /usr/share/games/flightgear/Aircraft/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Toni_Vines on 2014-05-06
Thank you both for your response. papibe, you're a star! That worked like a charm, thanks!

---

