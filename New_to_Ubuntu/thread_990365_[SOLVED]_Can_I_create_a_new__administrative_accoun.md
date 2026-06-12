---
title: "[SOLVED] Can I create a new  administrative account and delete the original"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-11-22
without breaking it? Can I also rename the computer?

My wife has taken possession of our aspire one so I might as well delete my account and make her one.

It used to be rob@rob-netbook.

It`s going to be suzie@suzie-netbook.

I Know how to go about doing this, just checking if I should.

Thanks.

---

### Post by wolfen69 on 2008-11-22
go to system>administration>users and groups. then unlock. then highlight the account you want to get rid of and click the delete button on the right. then click "add user" and add who you want. i've never renamed the computer, so not sure about that.

---

### Post by drs305 on 2008-11-22
Changing the computer name is simple. Edit /etc/hosts and /etc/hostname.

---

### Post by nothingspecial on 2008-11-22
Cheers. Like I said I know how to do it but I`ve never deleted the original account that I installed the system with. I don`t know if this is ok.

Is the original account inextricably linked to the installed system or can it be removed?

---

### Post by wolfen69 on 2008-11-22
if it was dangerous, i'm sure ubuntu would not have given you the option to delete accounts.

---

### Post by nothingspecial on 2008-11-22
Well here goes. I`ll set her account up before I remove mine and mark it solved if it`s all ok. Cheers

---

### Post by handydan918 on 2008-11-22
With Ubu, the only thing an "administrative" acount has is a listing in the /etc/sudoers file. 

As you stated you would do, just creating a new user and making sure they can "sudo" should be sufficient.

You wouldn't even need to delete yourself. That way you can read those e-mails from her b/f....

---

### Post by nothingspecial on 2008-11-22
> **handydan918 said:**
> 

You wouldn't even need to delete yourself. That way you can read those e-mails from her b/f....

I set up her e-mail, facebook etc etc anyway and I know her b/f well;)

Done it, rebooted no issue except after rm -rfing /home/rob I get

```
rm: cannot remove `/home/rob/.gvfs': Permission denied
```

So /home/rob still exists with that one directory in it. Any ideas? Cheers.

---

### Post by handydan918 on 2008-11-22
> **nothingspecial said:**
> I set up her e-mail, facebook etc etc anyway and I know her b/f well;)Well done, sir! Well said! Hah!> 

Done it, rebooted no issue except after rm -rfing /home/rob I get

```
rm: cannot remove `/home/rob/.gvfs': Permission denied
```

So /home/rob still exists with that one directory in it. Any ideas? Cheers.


```
sudo rm -rdf /home/rob
```

WARNING: EXECUTING THE ABOVE COMMAND WILL DESTROY YOUR SYSTEM IF YOU PUT A <SPACE> BETWEEN "/" AND "HOME"!!!!!111ONEONEONE!!!!!


?

:)

---

### Post by nothingspecial on 2008-11-22
> **handydan918 said:**
> ```
sudo rm -rdf /home/rob
```

WARNING: EXECUTING THE ABOVE COMMAND WILL DESTROY YOUR SYSTEM IF YOU PUT A <SPACE> BETWEEN "/" AND "HOME"!!!!!111ONEONEONE!!!!!


?

:)

Very true. Don`t do it unless you`re sure. Another reboot and the ne`re to be mentioned command worked. It`s all nice and pink now. Cheers guys, sometimes I just like to be sure myself.
[ATTACH]93748[/ATTACH]

---

### Post by handydan918 on 2008-11-23
Dude-
If that desktop is not a violation of some kind of rule....




it should be.









:lolflag:

---

