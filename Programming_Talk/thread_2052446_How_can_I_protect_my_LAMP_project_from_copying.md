---
title: "How can I protect my LAMP project from copying ?"
date: 2012-09-03
forum: Programming Talk
---

### Post by cherva on 2012-09-03
I have written an application that does a lot of stuff on php and I want to secure it from unauthorized copying. How can I do this ?

---

### Post by Bachstelze on 2012-09-03
Don't allow anyone access to your server at the file level (e.g. shell or FTP). PHP is parsed server-side, so HTTP clients (Web browsers) do not see your PHP source.

---

### Post by lisati on 2012-09-03
One possibility is through password protection, and have your server throw up 403 errors on failure. Combined with a tool such as fail2ban can help slow down rogues. There are different ways of doing this.

---

### Post by cherva on 2012-09-03
My bad I forgot to mention that this app will be on a client machine... I can't restrict access to php source or to the machine itself.... I was thinking about an usb dongle of some sort...

---

### Post by spjackson on 2012-09-03
> **cherva said:**
> My bad I forgot to mention that this app will be on a client machine... I can't restrict access to php source or to the machine itself.... I was thinking about an usb dongle of some sort...
If you give unrestricted access to source code and you have some code that tests for the presence of a usb dongle, how do you think you can prevent someone from removing that code from your source and just running the unprotected source?

Whatever physical scheme you decide upon, you will need to distribute a compiled binary to prevent your scheme being trivially circumvented.

---

### Post by cherva on 2012-09-03
I found phc [http://www.phpcompiler.org]("http://www.phpcompiler.org")
This will help me add the code for the dongle and compile it ... what do you think ? Any other ideas ?

---

### Post by snip3r8 on 2012-09-03
Facebook's open source hip hop compiler might do , it will also increase the performance. If i may as though , what is the point of running php client side? , all the same functionality could be achieved with javascript.

---

### Post by Lars Noodén on 2012-09-03
You could just make your requirements part of the licensing agreement with them.  Either you can trust them or you can't.

---

### Post by ofnuts on 2012-09-03
> **Lars Noodén said:**
> You could just make your requirements part of the licensing agreement with them.  Either you can trust them or you can't.
I second that.

---

### Post by Bachstelze on 2012-09-03
> **Lars Noodén said:**
> You could just make your requirements part of the licensing agreement with them.  Either you can trust them or you can't.

Users should never be trusted. Ever.

---

### Post by cherva on 2012-09-03
> **snip3r8 said:**
> Facebook's open source hip hop compiler might do , it will also increase the performance. If i may as though , what is the point of running php client side? , all the same functionality could be achieved with javascript.

It is a site that controls different devices and I want to sell that site... Can't keep it on my server, because noone will leave his credicentials on my server an for that reason I want to have their own copyes of the site ...

---

### Post by snip3r8 on 2012-09-03
In that case you will want to look into compilers or obfuscation as well as very limiting licences.

---

### Post by trent.josephsen on 2012-09-03
[quote=Learning Perl]If you're wishing for opaque binaries, though, we have to tell you that they don't exist. If people can install and run your program, they can turn it back into source code in any language. Granted, this won't necessarily be the same source that you started with, but it will be some kind of source code. **The real way to keep your secret algorithm a secret is, alas, to apply the proper number of attorneys; they can write a license that says, "You can do *this* with the source code, but you can't do *that*. And if you break our rules, we've got the proper number of attorneys to ensure that you'll regret it."**[/quote]

Bottom line is that there is no effective way to prevent people from copying your product. It didn't work for Windows, it didn't work for Minecraft, it didn't work for TV shows. You have to take the approach of making it *not worth the trouble* to copy the product.

Microsoft has a strict EULA and the lawyers to back it up. Minecraft is cheap enough that most people don't bother to pirate it. The entertainment industry keeps trying to make some kind of DRM work.

If you're trying to make money on this product, it might be worthwhile to look into providing support contracts; if people see it as an ongoing service, they're not likely to bother messing around with the code themselves (and having paid money for something can be a strong deterrent). Or figure a way to host the entire service yourself and charge for subscriptions.

---

### Post by cherva on 2012-09-04
The guys that are going to use it aren't very "hacker" minded so I need something simple to keep them down a little :) I'm sure that they won't be able to copy it ... but just to be a little more sure about a HDD copying :)

---

### Post by trent.josephsen on 2012-09-04
But if you can monetize it, what's to prevent someone who is relatively savvy from stealing it and underselling you, marketing it to the same end users? That's your real issue here. Everyday users are rarely the primary movers when it comes to software piracy.

---

