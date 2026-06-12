---
title: "Problem with Eclipse and the glassfish v2 server"
date: 2008-10-19
forum: Programming Talk
---

### Post by Starlight on 2008-10-19
Hello :)

I'm trying to learn JavaServer Faces and the Eclipse IDE, so I'm trying to do [this simple tutorial]("http://www.netbeans.org/kb/61/web/jastrologer-intro.html"), except that instead of NetBeans I'm using Eclipse 3.4. I have Glassfish v2 installed from the Ubuntu repositories, and Eclipse from the eclipse.org website. When creating the dynamic web project in Eclipse, it asked me about "target runtime". There was no Glassfish on the list, so I used "Download additional server adapters", where I found it and installed it. After restarting Eclipse, the GlassFish servers appeared on that list, and I picked GlassFish v2. Then, I started creating the JSF application in Eclipse, and everything went ok until I finally had to run it on the server. When I tried to run it, I got this error:

[IMG]http://i11.photobucket.com/albums/a156/Miracle86/Screenshot-2.png[/IMG]

It seems that there's something wrong with the admin port number. Here are the server options in Eclipse:

[IMG]http://i11.photobucket.com/albums/a156/Miracle86/Screenshot.png[/IMG]

It seems that the admin port is set to 1114848, but it seems to be uneditable. :( And it's the number kind of too large? What am I doing wrong here?

---

### Post by Starlight on 2008-10-19
This is REALLY weird. I found and edited my project's configuration file which is about the server, removing the "111" from port numbers. I saved it, opened Eclipse... but there the port numbers still have 111 in them :shock: And when I closed Eclipse, and opened the configuration file again, the numbers were without "111", just like they were after I edited them...

UPDATE: I installed NetBeans which came with its own Glassfish v2 server, and then I used that server in Eclipse. It's working well now :D Maybe it's because the one from Ubuntu repositories is installed in /usr/share where only root can write, and the one from NetBeans is in my home directory...

---

### Post by frapaa on 2009-12-18
I know this is an old thread, and I figure people will be annoyed of me updating it; but never the less:


I experienced the exact same thing, and the reason was improperly formatted config.xml. The port number was 8080, as with you, but I had added a property to enable comet support and forgotten to close the property tag (the final '/'):

```

<http-listener acceptor-threads="1" address="0.0.0.0" blocking-enabled="false" default-virtual-server="server" enabled="true" family="inet" id="http-listener-1" port="8080" security-enabled="false" server-name="" type="default" xpowered-by="true">
	<property name="cometSupport" value="true" **/**>
</http-listener>

```

I hope this will help you, or someone else, in the future!

Best regards,

Frank

---

### Post by kefas1209 on 2010-06-28
Hello,

the problem is that the eclipse is run by non-root user. Setting directory to glassfish domain rises non-validity messages. Even though domain.xml file had privilege to be read or to be written, it could not be read. Please check whether config directory of your domain has privilege to be listed (execute). If it doesn't have such, use chmod u+x config command. All the directories in path to domain.xml should have been given the right to be listed.
:)

---

