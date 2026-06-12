---
title: "Java File Writing Permissions"
date: 2007-08-18
forum: Programming Talk
---

### Post by thomasaaron on 2007-08-18
Ubuntu / Feisty
Netbeans

Hey, guys.

I'm having some permissions trouble with a java app I'm writing.
[B]
Here's the setup:[/B]

The application consists of a client-side GUI that accesses a server-side application. 

The server-side application is located in my Apache WebServer on the same computer (i.e. localhost, or /var/www).

The server-side application (in /var/www) needs to check for the existence of some files. If they do NOT exist, it creates them.

However, when it tries to create them, it fails with a "Permission Denied" error.

Obviously, I don't want to actually change the permissions of /var/www. So, what do I do?

**Here is what I've tried:**

1. I signed the .jar file for the app running on the server-side.

2. I used policytool to create an entry for the /var/www codebase.

I'm still getting the Permission Denied error, though.
How do I overcome this?

--------------------------------------------------------------------------------

Just did a little more testing...

I set the permissions of /var/www to read/write for everybody.
This allows the files to be created if necessary.
So, the problem is definitely permissions with the folder.
But how do I give my server-side app file-creation permissions?

---

### Post by laxmanb on 2007-08-18
ummm... you're using applets?? [policytool ]("http://java.sun.com/j2se/1.4.2/docs/tooldocs/windows/policytool.htm")should do the trick.But you've tried that...

and check whether Linux allows you to write files in those directories without root level permissions. Most directories outside your home directory are off limits to anyone except root...

---

### Post by DougB1958 on 2007-08-18
You didn't say how you start the server process -- is it possible that it is running as a user you don't expect, and that user doesn't have write access to /var/www?

---

### Post by CptPicard on 2007-08-18
I don't understand your setup, really. You've got a Java .jar *server-side* application on Apache :confused:

I mean... is that a Java web app that is running on Tomcat or something? That is, a .war? Or a servlet running on under JServ? Or something standalone? Or is this an applet, which is downloaded in a .jar like any other file, and is then run *client-side* in your browser, and then just tries to access/write files on the server using HTTP PUT? (I suspect this is your case, you're just stating it oddly -- all applet code is client-side!)

Generally speaking, there is no getting around file permissions... they are there for a reason. You do need to give permissions to whatever user the applet file writing happens under, otherwise the OS would be fairly compromised... 

You can, of course, see what user the writing happens under when you've given a+w, and analyze from there...

---

### Post by Tomosaur on 2007-08-18
/var/www should be owned by the www user. Thus, when you run your server app as www (which you should do), the app will have no trouble writing to that directory. Alternatively, create a new subdirectory and create a new user which has write access to this directory, then run your java app as that user.

---

### Post by thomasaaron on 2007-08-19
Thanks guys. I think you helped me figured this out. Let me just clarify a few things, and tell me if the solution makes sense.

About the application:

It is basically a two-part application (not an applet, servlet, or anything like that). One part of it runs on the client side, has a GUI that the user interacts with. The other part runs on the server-side. It receives information from the remote GUI via a network connection and stores that information in xml files in the /var/www directory.

Writing to the /var/www directory requires root permissions. So, if I start the server-side part of the application as root (i.e: sudo java -jar /var/www/SupportManager.jar), it now works perfectly and can write XML files within /var/www.

So, I mean, it works.

But is that the right way to do it?

Best,
Tom

---

### Post by laxmanb on 2007-08-19
Yeah... that seems about right.

also, I mentioned applets because policytool only works on applets and only applets work within a sandbox (no file system access without policytool permissions).

---

### Post by thomasaaron on 2007-08-19
Well, a little bit of both, actually.

Ultimately, it will store info to a MySql database. I'm creating the app to learn more about java. But I hope my employer will eventually implement it.

Even if they do not, though, I'm learning a lot about java.

Thanks for the tips. I'll definitely keep them in mind.


As a side note, I appreciate you guys answering my java questions here. It's harder than hades to get a newbie-level answer from the various java forums. I try to do due diligence in my own research, but sometimes it just helps to have somebody willing to break it down for you instead of giving you some vague high-level answer (or worse, grief).

So, thanks guys.

Best,
Tom

---

### Post by laxmanb on 2007-08-19
This seems like a good fit for an EJB on the server side. Do investigate that as an option when you make this app, K?

---

### Post by Tomosaur on 2007-08-19
No, no no :O

Do not run your server-side application as root. This means that the application has read/write access to every directory on your system. This is a security risk, and although there may be no code in your app which would actually allow it to write to somewhere other than /var/www, it's just a risk you shouldn't take.

The correct, and safest, way to do this is to create a new user / group (it may already exist) called 'www'. Give the www user ownership of the /var/www directory, and run your server-side app as this user. This will mean that your Java app can ONLY EVER write to the /var/www directory.

If you want to take it a step further, you could create another subdirectory owned by say, a user called 'javauser', and run your java app as that user. This will mean that the java app can only write to this sub-directory, and thus cannot over-write the rest of your website if something goes wrong.

---

### Post by laxmanb on 2007-08-19
^correct.

but in production, just use an EJB or Hibernate, etc. on an application server. You don't need to run the app server as root. The EJB will recieve information and store that in a MySQL table, so you'll have no problem with file permissions. The client and server GUIs interfaces should interact with the EJB when they have to perform a transaction [Saving the data, accessing the data, etc.].

---

### Post by thomasaaron on 2007-08-19
OOHHHHHHHH!

OK, now I see what you mean about creating a www user. That makes sense.

And I'll check out EJB too.

Thanks,
Tom

---

### Post by pmasiar on 2007-08-19
[EJB](http://en.wikipedia.org/wiki/Ejb) is usually overkill unless you write enterprise app, which I doubt because you would not be asking here for help. [POJO](http://en.wikipedia.org/wiki/Plain_Old_Java_Object) is another approach and is sufficient in most cases. See also [http://en.wikipedia.org/wiki/KISS_principle](http://en.wikipedia.org/wiki/KISS_principle) :-)

---

