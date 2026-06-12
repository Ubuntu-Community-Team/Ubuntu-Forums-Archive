---
title: "Cannot get the sudoers file to work..."
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Gizim on 2012-01-05
# User privilege specification
root    ALL=(ALL:ALL) ALL
myusername ALL=(ALL) NOPASSWD: ALL

Tried that tried

# User privilege specification
root    ALL=(ALL:ALL) ALL
myusername ALL=(ALL:ALL) NOPASSWD: ALL

and

# User privilege specification
root    ALL=(ALL:ALL) ALL
myusername ALL=(ALL:ALL) ALL

Still keeps asking for my password...

I even did a usermod -g admin myusername

Not sure what else to do..

---

### Post by TeoBigusGeekus on 2012-01-06
In my system (arch) it's:
```
username ALL=(ALL) ALL
```

I once encountered a similar problem with a friend's netbook and I solved it by changing the root password:
<snip>

---

### Post by KdotJ on 2012-01-06
> **TeoBigusGeekus said:**
> In my system (arch) it's:
```
username ALL=(ALL) ALL
```

I once encountered a similar problem with a friend's netbook and I solved it by changing the root password:
<snip>


But this still prompts you for your password though. I think the OP wants to be able to run root commands without having to enter their password.

---

### Post by TeoBigusGeekus on 2012-01-06
> **KdotJ said:**
> But this still prompts you for your password though. I think the OP wants to be able to run root commands without having to enter their password.

Yes, you're correct. I now remember that the problem was with gksu, not sudo.

@Gizim
Another thing to keep in mind is that you should always edit the sudoers file using visudo - you could otherwise cripple your system.

---

### Post by anewguy on 2012-01-06
PLEASE - We *DON'T* say on the forum how to set root password.  Please avoid mentioning this.


Dave

---

### Post by lisati on 2012-01-06
For the record (again), please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by KdotJ on 2012-01-06
> **lisati said:**
> For the record (again), please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I've never read or seen that before, thanks for the link it explained a few things.

---

### Post by Dangertux on 2012-01-06
Also it's 

```

usermod -a -G admin username

```

Hope this helps.

---

