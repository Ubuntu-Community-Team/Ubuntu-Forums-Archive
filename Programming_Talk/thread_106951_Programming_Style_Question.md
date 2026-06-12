---
title: "Programming Style Question"
date: 2005-12-21
forum: Programming Talk
---

### Post by darthsabbath on 2005-12-21
Hi, all,

I've got a question and I'm not QUITE sure how to put it... so let's just jump straight in... say I'm working with a library, we'll use Python's poplib for this example.  Is it better to simply use the methods define by the library directly, such as...

```

# Let's connect to the host now
session = poplib.POP3(host, port)
session.user(login)
session.pass_(pass)

```

Or is it better to add another level of abstraction to this mix by grouping all of the POP3 functions into their own class, as in the following?

```

class POP3Session:
	def ConnectHost(self):
			self.session = poplib.POP3(self.host, self.port)
			self.session.user(self.login)
			self.session.pass_(self.pwd)


```

Functionally, there's no difference.  But is it wasteful to do this grouping, or pointless, or does it serve to make the program better organized?  

Sorry I haven't been clear... I know WHAT I'm asking, I'm just not quite sure how to ask...

Phil

---

### Post by skirkpatrick on 2005-12-21
Go with the first one.  There's no need to add an additional level of abstraction.

---

### Post by Van_Gogh on 2005-12-22
If the code is small I don't do it. But if it gets just somewhat large, I usually group, into either functions or classes, if for no other reason just to keep the global name space clean.

---

### Post by thumper on 2005-12-22
If you are wanting to always to additional processing for certain steps, then it may make sense to abstract that away behind another object.

In the simple case, you are not adding anything but more code.

There is no bug in no code.

---

### Post by LordHunter317 on 2005-12-22
It depends.  If you're trying to provide higher-level behaviors to the rest of your application, then you should provide a class that uses the POP3 library and  provides those higher-level behaviors.  That way, the fact you're using POP3 is both abstracted and encapsulated.

---

### Post by darthsabbath on 2005-12-22
Thanks for responding guys...

The example code I supplied above is very simple... the actual class I'm coding involves logging/dugging messages as well as exception handling, encapsulating it all in it's own hidey hole.

I guess I should've explained that in my original post. :-)

Phil

---

### Post by Jengu on 2005-12-23
I would say it depends on how much you're trying to do. If you want to code an e-mail app that can handle POP3 *and* IMAP, you might have a generic Connection class that POP3Session and IMAPSession inherit from. This way then your "Check my e-mail" code only has to be written once for Connection.

But if you're just writing a quick script, or know you only want one connection type, don't bother.

---

