---
title: "How to open /etc/sysctl.conf in an editor?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by dkinthehouse on 2012-04-09
Hey Everyone, I'm on 11.10.  What steps should I take to open /etc/sysctl.conf?  Can I use sudo or do I need to be in root?  Ideally I'd like to use gedit but that I couldn't seem to open the file in gedit.  Help.  Thanks.

---

### Post by llua+ on 2012-04-09
gksu gedit /etc/sysctl.conf

---

### Post by oklokl on 2012-04-09
[COLOR=Red]Please note .
If you incorrectly modify the system error[/COLOR]

ctrl alt T

view..
cat /etc/sysctl.conf


backup
Will first

sudo cp -rf /etc/sysctl.conf /etc/sysctl.conf.bak

sudo gedit /etc/sysctl.conf

or

sudo nano /etc/sysctl.conf

or..

sudo vi /etc/sysctl.conf

or..

sudo -i
gedit /etc/sysctl.conf
exit..

ctrl D
2 Twice

testing

route

or

route -6





Easy..
 How to Change
save user.. file

sudo sh -c "echo cat *sysctl.conf*(you file* ) > */etc/sysctl.conf"
ex>

sudo sh -c "echo cat *~/Downloads/sysctl.conf** > */etc/sysctl.conf"



and Tip...

sudo gedit error.. Message  -> [http://ubuntuforums.org/showthread.php?t=1788133](http://ubuntuforums.org/showthread.php?t=1788133)
sudo mkdir /root/.local /root/.local/share


or Tip.. ipv6 deny

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
[http://en.kioskea.net/faq/759-ubuntu-disabling-ipv6-support](http://en.kioskea.net/faq/759-ubuntu-disabling-ipv6-support)
[http://blog.saltfactory.net/category/Unix/Linux](http://blog.saltfactory.net/category/Unix/Linux)
[http://ubuntuforums.org/showthread.php?t=1312082](http://ubuntuforums.org/showthread.php?t=1312082)
#[http://superuser.com/questions/33196/how-to-disable-autoconfiguration-on-ipv6-in-linux](http://superuser.com/questions/33196/how-to-disable-autoconfiguration-on-ipv6-in-linux)

echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf

---

### Post by bodhi.zazen on 2012-04-10
> **oklokl said:**
> 

view..
cat /etc/sysctl.conf

less is probably better for this task.

```
less /etc/sysctl.conf
```

> backup
Will first

sudo cp -rf /etc/sysctl.conf /etc/sysctl.conf.bak

Well, for backups, you probably want -i rather then -f

-f will over write any previous backup, which is probably not the behavior you want.

> sudo gedit /etc/sysctl.conf

for graphical applications, such as gedit, you should use gksu

```
gksu gedit /etc/sysctl.conf
```

> or

sudo nano /etc/sysctl.conf

or..

sudo vi /etc/sysctl.conf

What about sudo -e ?

```
sudo -e /etc/sysctl.conf
```

> or..

sudo -i
gedit /etc/sysctl.conf

As above, use gksu

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)


> Easy..
 How to Change
save user.. file

sudo sh -c "echo cat *sysctl.conf*(you file* ) > */etc/sysctl.conf"
ex>

sudo sh -c "echo cat *~/Downloads/sysctl.conf** > */etc/sysctl.conf"

Not sure what you are trying to do here, but:

1. No need for 'echo cat', just cat .

2. cat file > file_2 can be simplified to cp file file2

3. To append, use >>

```
cat file >> file2
```


> and Tip...



did not review those tips.

---

### Post by oklokl on 2012-04-10
Good point, thanks.

The reason I  
cp -rf.
 Extensively used
(This is useful when copying directories.)
(General users will give up little things.) error..
I think it is accurate to cp-f .. Under normal circumstances, this does not actually write.


Only the terminal
 Is a command.
 Please note that the benefits ...

cat 1.txt > 1.txt   
full change file
Press to change too much detail

sudo -e ???
This sentence is from where?

---

### Post by mc4man on 2012-04-10
> **bodhi.zazen said:**
> 
for graphical applications, such as gedit, you should use gksu

```
gksu gedit /etc/sysctl.conf
```


I've no doubt you know better than me, so just to mention

I don't think I've ever seen any indication that sudo gedit is an issue that would be better served by using gksu(do)

Or alternately possibly just use (suggest),  sudo -H gedit <whatever>

The reasoning is that with gnome3 gksudo gedit always opens a 2nd 'untitled' document which is generally a pita & possibly could confuse some users as to why & what to do with.

---

### Post by Ms. Daisy on 2012-04-10
This is something I've been wondering about, I'm glad it came up.  The link in bodhi's post says this
> You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo). 
Can anyone say WHY it would be terrible if root owned files in the home directory?

---

### Post by oklokl on 2012-04-10
I admit everything.  error..
sorry..
Sorry we couldn't help
I wanted to help and
I does not use. gksudo ..
[http://cafe.daum.net/candan](http://cafe.daum.net/candan)
my home..

Kubuntu does not use.
Ubuntu will only use only.

---

### Post by Cheesemill on 2012-04-10
> **Ms. Daisy said:**
> This is something I've been wondering about, I'm glad it came up.  The link in bodhi's post says this

Can anyone say WHY it would be terrible if root owned files in the home directory?
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

I've had to talk people through fixing problems that have been caused by just this issue, for example:
[http://ubuntuforums.org/showthread.php?t=1915537](http://ubuntuforums.org/showthread.php?t=1915537)

---

### Post by oklokl on 2012-04-10
First-time users
 From the terminal
 Use sudo gedit
sorry
I&#8217;m not very good with computers

---

### Post by Cheesemill on 2012-04-10
> **oklokl said:**
> First-time users
 From the terminal
 Use sudo gedit
sorry
I’m not very good with computers
As already mentioned above you should always use gksudo instead of sudo with graphical applications.
```
gksudo gedit /etc/sysctl.conf
```

---

### Post by Ms. Daisy on 2012-04-10
> **Cheesemill said:**
> [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

I've had to talk people through fixing problems that have been caused by just this issue, for example:
[http://ubuntuforums.org/showthread.php?t=1915537](http://ubuntuforums.org/showthread.php?t=1915537)
Thank you, great info!

---

### Post by bodhi.zazen on 2012-04-10
> **mc4man said:**
> I've no doubt you know better than me, so just to mention

I don't think I've ever seen any indication that sudo gedit is an issue that would be better served by using gksu(do)

Or alternately possibly just use (suggest),  sudo -H gedit <whatever>

The reasoning is that with gnome3 gksudo gedit always opens a 2nd 'untitled' document which is generally a pita & possibly could confuse some users as to why & what to do with.

Then you should read more =)

I posted a link for reference as did others.

> **Ms. Daisy said:**
> This is something I've been wondering about, I'm glad it came up.  The link in bodhi's post says this

Can anyone say WHY it would be terrible if root owned files in the home directory?

Ms. Daisy is spot on as usual. 

From the rootsudo wiki page :

> You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).

Although , as sudo uses the wrong value for $HOME, .Xauthority is not the only file that can be problematic.

See also

[http://www.gratisoft.us/sudo/sudo.man.html](http://www.gratisoft.us/sudo/sudo.man.html)

[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

Pay attention to environmental variables ;)

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by dkinthehouse on 2012-04-10
Awesome.  Thanks everyone.  I tried gksu and it worked great.  Interesting discussion.

---

