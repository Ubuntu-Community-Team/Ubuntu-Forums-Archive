---
title: "How to logout from public key authentication - ssh"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by karthick87 on 2011-12-08
I am using key based authentication for ssh. When ever i try to login into the system it doesn't ask me for public key. It simply logs in, i just want to logout from this public key authentication. And when ever i need i will enable it. Can some one say me the way to logout from Public Key authentication. And How to set timeout for this public key authentication? Thanks in advance.

---

### Post by Lars Noodén on 2011-12-08
You can cancel an identity in the agent using [ssh-add](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-add.1.html).  [font=Courier New]-D[/font] will cancel all identities, or a specific one can be cancelled with [font=Courier New]-d[/font]

```

# cancel all
ssh-add -D

# cancel one
ssh-add -d /home/karthick87/.ssh/*somekey_rsa*

```

You can set the timeout period for key based authentication by passing the [font=Courier New]-t[/font] option in [ssh-agent](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-agent.1.html) or when you add the identity in [font=Courier New]ssh-add[/font].  

I'm not sure where Ubuntu launches [font=Courier New]ssh-agent[/font] from, but if you find it, that's where to make the changes globally from.

---

### Post by karthick87 on 2011-12-08
Thank you Lars, but what is the default timeout?

---

### Post by Lars Noodén on 2011-12-08
If the default timeout is not specified, then it is forever.  It can be specified by [font=Courier New]ssh-add[/font] when you add the key.  That might be the way until we can find where [font=Courier New]ssh-agent[/font] is launched from.

---

