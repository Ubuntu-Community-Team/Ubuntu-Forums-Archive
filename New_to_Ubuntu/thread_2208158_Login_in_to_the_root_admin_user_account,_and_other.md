---
title: "Login in to the root admin user account, and other tty's"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by Weedy101 on 2014-02-26
I am a noob to Ubuntu, using 12.04LTS. I have been making use of the many tutorials posted in the Ubuntu forums and other Ubuntu/Linux official resources. Several tutorials have discussed topics such as the other tty terminal windows - F1 -> F9 etc - and they have also discussed the 'su' command.

I installed this os on this system and only set up 1 password which I use to login, when I use 'sudo' I use the same password, but when I want to use 'su' or one of the other tty windows I can't log in to them. I also can't log directly into the root account (superuser) for admin and have limited access to some commands when using 'sudo'.

When trawling through the many configuration files looking for possible reason's why this would be I have come accross a couple of references to "john" having access to all area's. I know not who john is and am assuming this is a default or sudaname that the system is using. I have also found reference to my own user having acces to most but not all area's of the system.

My question is how can I login to 'su' or the other tty windows? Is there a configuration file somewhere that I have yet to set up/adjust to get these things working, and if so where is it and what settings should I use?

Also what, or who is the "john" that I have come accross in configuration files?:confused:

---

### Post by lykwydchykyn on 2014-02-26
- Root account is disabled in Ubuntu, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
- If you need a root shell, just use "sudo -i". 
- You can get to your TTY's by hitting ctrl-alt-F1 through ctrl-alt-F6.  Your Graphical desktop is typically on ctrl-alt-f7 or ctrl-alt-f8.

There is no default user "john" AFAIK.  Can you post an example configuration containing "john"?

---

### Post by Weedy101 on 2014-02-26
> # User "root" should be denied to get access from all other sources.
#- : root : ALL
#
# User "foo" and members of netgroup "nis_group" should be
# allowed to get access from all sources.
# This will only work if netgroup service is available.
#+ : @nis_group foo : ALL
#
# User "john" should get access from ipv4 net/mask
#+ : john : 127.0.0.0/24
#
# User "john" should get access from ipv4 as ipv6 net/mask
#+ : john : ::ffff:127.0.0.0/127
#

This is an excert from 'access.conf' in my /etc/security folder. It also mentions 'foo' as a user but I know there are some special meanings to the foo and foomatic name which I was not going to be looking into just yet as it's a bit to advanced for me.

The tty's I know how to get to them but when I go to one of them I am asked to log in - my log in does not work.

As to the 'sudo -i' that works perfectly, shame I couldn't find that in the man and info files :(
I will have a good read of the 'RootSudo' link you posted and any related post's I can find on that site as well thanks.

---

### Post by twilkins111 on 2014-02-26
Use sudo passwd root in the terminal. That command will then prompt ou to change your password. it will ask ou to type the new one twice. then simply type su then the password that you changed it too.

---

### Post by The Cog on 2014-02-26
I advise against setting a root password. It breaks some security assumptions used in Ubuntu (that there is no direct root login). As Weedy101 says, log in as normal and use the command **[FONT=Courier New]sudo -i[/FONT]**.

What do you mean "my log in does not work" with the ttys? Is the fact that there is no echo as you type the password confusing you? 

Another less likely possibility is that the GUI and TTY keyboard settings are different. Could it be a language/layout issue?

---

### Post by lisati on 2014-02-26
Enabling the root password is usually discouraged here in the forum, due to the unintentional damage that can be done. For most purposes, **sudo** or **sudo -i** will suffice.

---

### Post by Weedy101 on 2014-02-26
> **The Cog said:**
> I advise against setting a root password. It breaks some security assumptions used in Ubuntu (that there is no direct root login). As Weedy101 says, log in as normal and use the command **[FONT=Courier New]sudo -i[/FONT]**.

What do you mean "my log in does not work" with the ttys? Is the fact that there is no echo as you type the password confusing you? 

Another less likely possibility is that the GUI and TTY keyboard settings are different. Could it be a language/layout issue?

Whenever I go to one of the other TTY's it prompts me to login, when I try to login I get 'Login incorrect' or 'Login failed'. However I have just tried going to one of the other TTY's while using 'sudo -i' and the login worked. This is confusing, but as long as I can always use the 'sudo -i' before going to another TTY the problem is solved.

As to suggestions of creating a password for root, or activating root - Not a chance, especially as a noob - to easy to break things without realizing what you are doing. So Twilkins111 I recommend you read the post about RootSudo which I am glad to have been offered before your reply.

---

### Post by lykwydchykyn on 2014-02-27
> **Weedy101 said:**
> This is an excert from 'access.conf' in my /etc/security folder. It also mentions 'foo' as a user but I know there are some special meanings to the foo and foomatic name which I was not going to be looking into just yet as it's a bit to advanced for me.


All those lines are commented, meaning they aren't read by the system.  They're there to give you examples of how you can configure things.
Config files vary in syntax, but in general starting a line with a "#" makes it a comment, which means it's there for you to read and the system to ignore.

"foo" along with "bar", "baz", and other nonsense words are just placeholder words that programmers like to use, sort of like mathemeticians use X or N.
You can read more here: [http://www.catb.org/jargon/html/F/foo.html](http://www.catb.org/jargon/html/F/foo.html) (warning: bit of foul language in that article, sorry).

---

### Post by mkg2 on 2014-12-08
Simply type 'root' as the username and proceed with your root password. You have probably tried using your host-name, domain-name, and standard username . Up to this point, only your standard username and corresponding password worked, but then you could not execute root commands, even with sudo -i etc because your standard username is not in the sudoers file by default. This is happening simply because you created the standard user account, which is reccomended. And if you had not installed, or were planning not to install, a graphical interface by this time... it would seem as though you were stuck, but have no fear: root [ENTER] root password [ENTER] and proceed with terminal commands as usual.

---

### Post by lisati on 2014-12-08
> **mkg2 said:**
> Simply type 'root' as the username and proceed with your root password. You have probably tried using your host-name, domain-name, and standard username . Up to this point, only your standard username and corresponding password worked, but then you could not execute root commands, even with sudo -i etc because your standard username is not in the sudoers file by default. This is happening simply because you created the standard user account, which is reccomended. And if you had not installed, or were planning not to install, a graphical interface by this time... it would seem as though you were stuck, but have no fear: root [ENTER] root password [ENTER] and proceed with terminal commands as usual.

As has been previously mentioned, the root account is disabled by default in Ubuntu.

---

