---
title: "is ubuntu secure enough for a newbie?"
date: 2009-10-18
forum: Recurring Discussions
---

### Post by insanity99 on 2009-10-18
i can basically to anything to my system by typing 'sudo'and proving a password that i setup. if some one told someone like me to do something like rm '-rf /' a few weeks ago i would have done so without a second thought because i trust this community. 

i was just wondering if it would be better to require a root login, like fedora.

thanks

---

### Post by CharlesA on 2009-10-18
Root is disabled by default in Ubuntu, you can enable it, but imho it's more of a security threat then not.

Besides, it wouldn't really help. When you use sudo, you run as root for all intents and purposes. Just watch what you run as the super user and you'll be ok.

If you want a certain user not to have admin rights, remove them from that group. which removes them from the sudoers file as well.
[SIZE=1]
I should know, I screwed up and did that to myself, was a pain in the butt to fix (thank goodness that I imaged the drive when I got the machine up and running.[/SIZE]

---

### Post by iKonaK on 2009-10-18
Well sudo or root is kinda the same thing, sudo it's just more convenient and simple.
Regarding the rm command, I believe that users should always do a man page check before sending a command and if you would to get the rm command in this community the user who gave you that (whit out explaining)  would be kicked out.

---

### Post by 3rdalbum on 2009-10-18
> **insanity99 said:**
> i can basically to anything to my system by typing 'sudo'and proving a password that i setup. if some one told someone like me to do something like rm '-rf /' a few weeks ago i would have done so without a second thought because i trust this community. 

i was just wondering if it would be better to require a root login, like fedora.

It would be worse, if you think about it. People would decide "Well, I hate these constant 'permission denied' errors, so I'll just always log in as root rather than switch user".

We already get a small number of people asking how to "remove the constant password prompts" and enable the root account.

---

### Post by Soul-Sing on 2009-10-18
using: ubuntu software-sources
       sudo (no root) priv.
       desktop (no server) environ. To setup a server a not difficult but needs far more sec. focus, and understanding.
       install always sec. updates

---

### Post by juancarlospaco on 2009-10-18
Theres no root to attack if theres no root :)

---

### Post by viper250 on 2009-10-18
as a system administrator in both linux and windows systems I have to tend to multiple users because of this i routinely change passwords including my own.
consider for security purposes myself I do not use windows but must maintain them at work. while some linux distros by default will set up with both root and user accounts some do not and even those you can configure with multi level accounts:guitar:

---

### Post by Regenweald on 2009-10-19
> **insanity99 said:**
> i can basically to anything to my system by typing 'sudo'and proving a password that i setup. if some one told someone like me to do something like rm '-rf /' a few weeks ago i would have done so without a second thought because i trust this community. 

i was just wondering if it would be better to require a root login, like fedora.

thanks

I think the responsibility lies with the user. The type of user that blindly runs commands may well be the same type that double clicks a clickme.exe.txt attachment.

look at zenbuntu, comes with pre designed apparmor profiles. Apparmor is one of the big boys in security. But what if a user follows a shady tutorial and one of the steps is to disable apparmor ?

The most powerful security solution is only as strong as it's administrator. Common sense and education are you best security.

---

