---
title: "Added myself to group, removed me from all others"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by starstreams on 2013-01-19
I looked through the man pages, but could not find the -G flag I used, demonstrated on a site.
I created a group called *mygroup*, and when I added my username to the group via terminal, it removed me from all other groups, including sudo. (But I "was" added to the new group).
```
sudo usermod -G mygroup myusername
```I added myself back into the sudoers file from the recovery root prompt so everything is back to normal. But I'm curious, why did this remove me from all other groups before adding me to my new group?
I know I could have just opened the groups config file and preformed the task there, but I just wanted to try the command. I thought the usermod command was to add an existing user to a group, while adduser is for adding a new user, among other things.

As noted [here]("http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/") under the section titled:
[B][SIZE=2]usermod example - Add a existing user to existing group
[/SIZE][/B][SIZE=2][SIZE=2][SIZE=2]It looks like maybe I should have used a lower case -g? I[SIZE=2]f I'm understanding[SIZE=2] correct?[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][B][SIZE=2]
[/SIZE][/B]

---

### Post by bab1 on 2013-01-19
> **starstreams said:**
> I looked through the man pages, but could find the -G flag I used, but it was in a book I was reading.
Anyway, I created a group called *mywork*, and when I added my username to the group via terminal, it removed me from all other groups, including sudo.
```
sudo usermod -G mywork myusername
```I added myself back into the sudoers file from the recovery root prompt so everything is back to normal. But I'm curious, why did this remove me from all other groups before adding me to my new group?
I know I could have just opened the groups config file and preformed the task there, but I just wanted to try the command. I thought the usermod command was to add an existing user to a group, while adduser is for adding a new user, among other things.

As noted [here]("http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/") under the section titled:
**[SIZE=2]usermod example - Add a existing user to existing group[/SIZE]**

From the man pages```

-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of. 
Each group is separated from the next by a comma, with no intervening 
whitespace. The groups are subject to the same restrictions as the group 
given with the -g option.

           [B][COLOR="Red"]If the user is currently *_a member of a group which is not listed_*, 
the user will be *_removed_* from the group.[/COLOR][/B]

[COLOR="Blue"][B]This behaviour can be *changed via the -a option*, which *_appends_* the user 
to the current supplementary group list.[/B][/COLOR]

In short, If you want to add a user you should use **[COLOR="Blue"]-a[/COLOR] [COLOR="Red"]-G [/COLOR]**

```

---

### Post by sisco311 on 2013-01-19
EDIT: D'oh! bab1 beat me to it. :)

You have to use the -a flag to add the user to supplementary groups:
```
usermod -aG group user
```

From **man usermod**

```

...
       -a, --append
           Add the user to the supplementary group(s). Use only with the -G
           option.

...
       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.

           If the user is currently a member of a group which is not listed,
           the user will be removed from the group. This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.


```

---

### Post by starstreams on 2013-01-19
Thank you, bab1, and sisco311
I was searching all the group man pages except the one I needed: usermod.
Looks like it clearly explained the -a flag.

Thanks guys
Makes complete sense now.

---

### Post by starstreams on 2013-01-19
I created some kind of new issue related to the previous post above.
When I accidentally removed myself from all other groups the previous night, today I added myself back to all the groups the system had originally assigned:
```
sudo usermod -a -G adm,dialout,cdrom,floppy,audio,dip,src,video,plugdev,fuse,lpadmin myusername
```I have confirmed that I "am" once again assigned to the groups listed in the code above by viewing the etc/group file, however now when I re boot I keep getting this authentication message that says: "[COLOR=Red]*An applications  want's to add a password to the keyring called: Default*[/COLOR]".

I read somewhere that if you just hit enter to the blank password prompt it stores the system wide password insecure. So instead (I entered a password).  This is a GUI window that pops up by he way so it's probably not saving my password because I'm logged in as a standard user. However, I don't know what this keyring prompt is and why all the sudden I'm being prompted with it now? Something must have changed when I previously removed myself from all other groups. I don't know how to access this keyring popup as a root user to save the password or if that's even what I should be doing? Not even sure if I should just use my Wifi password or choose another. Either way, entering a password made no difference. I'm still getting the popup.

---

### Post by starstreams on 2013-01-23
I seemed to have resolved the issue in post #5 by deleting the 

~/.gnome2/keyrings/Default.keyring

---

