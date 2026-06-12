---
title: "Installing VLC"
date: 2015-01-08
forum: New to Ubuntu
---

### Post by Victor_Gilbert on 2015-01-08
I installed VLC from Software Centre. I then installed ubuntu-restricted -extras .... libdvdread4 ...... libdvdnav4 from the Software Centre. When I press play button immediately pause appears.
Can somebody help?.

Victor

---

### Post by ajgreeny on 2015-01-08
When you press Play the icon changes to the Pause icon (two vertical lines) to allow you to pause the music or video.
Are you saying that the music or video stops, or doesn't even start when you click on play?

---

### Post by Victor_Gilbert on 2015-01-08
.Hi ajgreeny
 Thatis what happens      "or doesn't even start when you click on play?"

---

### Post by westie457 on 2015-01-08
> **Victor_Gilbert said:**
> I installed VLC from Software Centre. I then installed ubuntu-restricted -extras .... libdvdread4 ...... libdvdnav4 from the Software Centre. When I press play button immediately pause appears.
Can somebody help?.

Victor
Did you run this command after installing the above?
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I had the same problem about 4 weeks ago and that command fixed things for me.

---

### Post by Victor_Gilbert on 2015-01-08
Thanks Westie 457

Entered command in (ctrl + alt+ T) , pressed enter. Unable to enter the first and subsequent letters of my password!!!!

---

### Post by sudodus on 2015-01-08
There is no echo of the password (you see no dots), but it is entered anyway. Try again (enter the password and finish with the Enter key) :-)

---

### Post by Victor_Gilbert on 2015-01-08
Hi Westie 457

Solved the problem of typing password .... It's typed but doesn't show up!!!!!
Entered ....*.sudo /usr/share/doc/libdvdread4/install-css.sh* followed by password.

At the end of all the commands came:

victor@victor-Extensa-E210:~$ (Flashing Cursor)...... Something reqired of me ...... But what??

Victor

---

### Post by sudodus on 2015-01-08
The prompt **victor@victor-Extensa-E210:~$** has returned and the terminal is ready for another command (for example exit to close the terminal window).

---

### Post by Victor_Gilbert on 2015-01-08
Great Sudodus

Wow! Did it.

Thanks 

Victor

---

### Post by Juan_Carless on 2015-01-10
Thanks a bunch!!  This works for me too!

---

### Post by Sef on 2015-01-10
> [COLOR=#000000]Solved the problem of typing password .... It's typed but doesn't show up!!!!![/COLOR]

Often with Linux, the password does not show up.  This is a security feature, so if someone cannot know how many keys were pushed to input the password.

---

