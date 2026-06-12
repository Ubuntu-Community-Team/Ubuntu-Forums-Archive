---
title: "moving to the folder containing the script itself"
date: 2008-05-15
forum: Programming Talk
---

### Post by mizar001 on 2008-05-15
Hi. A little problem in bash scripting.
When i launch a script from anywhere, can i use code to move to the real directory of the script before doing anything ?

---

### Post by bvmou on 2008-05-15
I think you can do this by just putting a 'cd' in the script.  So, for example:

cd ~/Desktop
cp *.jpg /media/disk/pics
cd ~/pictures
cp *.jpg /media/disk/pics

Is this what you mean?

If you just want to work with what directory you are in, the syntax is `pwd` (where the quotes are next to the 1 on an English keyboard.) So for example, if you wanted to make an alias that would copy the mp3's from whatever directory you were in to your Desktop, you could edit your .bashrc file to include a line like[PHP] alias mp3copy='cp `pwd`/*.mp3 ~/Desktop'[/PHP]  Does that help?

---

### Post by mizar001 on 2008-05-15
I want to call the script from anywere , so with $(pwd) i can't resolve this problem because the 'pwd' command print the current directory and not the actually dir of the script. I can change it , but i can't know for sure where the script is located if i don't parse the call ($0 parameter).

Example :
mizar@mizarpc:/opt/apache$  /home/user/dir/.../script.sh 

inside the script the 'pwd' command give me the '/opt/apache' string.
I want it to give me the /home/user/dir/.../ path instead, without a static leading 'cd' command at beginning, or the path that this link is pointing to.

---

