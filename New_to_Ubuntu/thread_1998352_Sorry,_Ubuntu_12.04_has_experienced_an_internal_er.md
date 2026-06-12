---
title: "Sorry, Ubuntu 12.04 has experienced an internal error /usr/bin/Xorg"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by cwmoser on 2012-06-06
I got this error logging into Ubuntu 12.04 64-bit:

[B]Sorry, Ubuntu 12.04 has experienced an internal error 
/usr/bin/Xorg[/B]


Is there a fix????

Thanks

Carl

---

### Post by Viper1987 on 2012-06-06
Try renaming the xorg.conf to xorg.conf.backup. Reboot

this file can be found in /etc/X11/xorg.conf

---

### Post by NikTh on 2012-06-06
> **Viper1987 said:**
> Try renaming the xorg.conf to xorg.conf.backup. Reboot

this file can be found in /etc/X11/xorg.conf
+1 

try also  from VT
```
sudo service lightdm stop 
sudo dpkg-reconfigure xorg xserver-xorg xserver-xorg-core 
sudo service lightdm start
```

---

### Post by zcacogp on 2012-06-09
Chaps, 

I'm having the same problem on several machines, some of them with 32-bit and some with 64-bit. 

Trying this fix on this machine I find that I don't seem to have an xorg.conf. Which seems odd ... could this be the problem? 


Oli.

---

### Post by kuramayoko10 on 2012-12-01
I was working on my desktop with Ubuntu 12.04 64-bit and then it froze for a while. Then it got back to the login screen.

After logging in it gave me the exact same error.
I did the suggested above and I am waiting to see if the problem happens again.

Was it coincidence that his happened a little after I changed the number of Desktop Workspaces in CompizConfig Settings Manager?
I just set it to 6 horizontal virtual worksaces and 1 Desktop.

---

### Post by DaVince21 on 2012-12-01
> **zcacogp said:**
> Chaps, 

I'm having the same problem on several machines, some of them with 32-bit and some with 64-bit. 

Trying this fix on this machine I find that I don't seem to have an xorg.conf. Which seems odd ... could this be the problem? 


Oli.

This could not be the problem. xorg.conf isn't required - it's just that when it exists, it might have contained some faulty/conflicting configuration. The problem probably lies elsewhere, like maybe the graphics driver is just faulty.

---

### Post by monkeybrain2012 on 2012-12-01
Do you actually experience any problem or just an error message? It could be a false alarm. 

[http://askubuntu.com/questions/142016/sorry-ubuntu-12-04-has-experienced-an-internal-error](http://askubuntu.com/questions/142016/sorry-ubuntu-12-04-has-experienced-an-internal-error)

Last week someone reported on this forum that he actually got an internal error message about Apport itself(the error reporting software in question) :) I have turned it off.

---

### Post by kuramayoko10 on 2012-12-01
I have not noticed any problems after that quick freeze my desktop suffered.

But I think the error was a false alarm because I got another one that was false alarm as well.
The link monkeybrain2012 posted explains it, but I will quote the answer in this post as well:
> Apport is used in alpha and beta releases to help find and report  bugs and would normally be switched off in a final release, but for some  reason I have noticed it is on in 12.04.
  This is causing unnecessary crash reports to pop up and it will be completely safe to turn off
  To turn off Apport, run:
sudo sed -i s/enabled=1/enabled=0/ /etc/default/apport


---

### Post by squakie on 2012-12-01
+1.  Since I installed 12.x, I've had literally hundreds of these error messages (not just X) pop up, and in my case they are all false hits.  It's a bug.

---

### Post by bogan on 2012-12-02
**Hi!,** All

I too have had many, apparently spurious, Apport "Ubuntu has experienced an !nternal Error" reports, since 12.04 was released, and similarly in 12.10, though not so many.

However, with this last Error message quoting XORG, it was not spurious. It followed an update to xserver-xorg-core, and on rebooting hung up in the Greeter Login screen - as the OP reported - returning to the Password Requestor after entering the correct password.
When I used```
 # 'Ctrl+Alt+F1' and:
sudo service lightdm stop # followed by:
startx
```I got an: 'xinit: Fatal Error: GLX not found' error message and it froze.

After trying several obvious steps, unsuccessfully, I re-installed the nvidia 304.51 driver, and had it renew the xOrg.conf file, and that cured the problem. 

Following re-boots, I re-ran 'startx' to be sure there were no error messages, and it operated correctly.

Chao!,** bogan.**

---

### Post by NikTh on 2012-12-02
> **squakie said:**
> +1.  Since I installed 12.x, I've had literally hundreds of these error messages (not just X) pop up, and in my case they are all false hits.  It's a bug.

Hi , 
maybe you have a point here. If you are sure that are **false messages from apport** then you can **disable the reports** with this command 

```
sudo sed 's/enabled=1/enabled=0/' -i /etc/default/apport
```Thanks

---

### Post by bogan on 2012-12-02
Hi!,** NikTh**,

Copy/Pasting your command gives 'no such file or directory'.

Presumably "approt" is a 'typo' for "apport".

My '/etc/apport' currently reads:```
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=0
```Which is, to say the least, ambigious, not to say contradictory.

After running your command [corrected] it remains unaltered; but the 'Apport' messages occurred despite 'enabled' being set to '=0'.

Chao!, **bogan**.

---

### Post by NikTh on 2012-12-03
> **bogan said:**
> 
Copy/Pasting your command gives 'no such file or directory'.

Presumably "approt" is a 'typo' for "apport".
Yeap , sorry for typo and thanks you mentioned. 

> **bogan said:**
> My '/etc/apport' currently reads:```
**# set this to 0 to disable apport**, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=0
```

> **bogan said:**
> After running your command [corrected] it remains unaltered; but the 'Apport' messages occurred despite 'enabled' being set to '=0'.


As you can see the instructions are "set this to 0 to disable apport" , and I think you have to reboot for changes to take effect.

---

