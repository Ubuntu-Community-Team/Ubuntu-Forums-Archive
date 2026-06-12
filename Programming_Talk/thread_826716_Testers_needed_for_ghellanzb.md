---
title: "Testers needed for ghellanzb"
date: 2008-06-12
forum: Programming Talk
---

### Post by nico_open on 2008-06-12
Hello,

This is my first thread.

I am currently developing a gnome applet in Python called  [ghellanzb ]("http://nicoworkspace.free.fr/?q=ghellanzb-home"). It is designed to retrieve [hellanzb]("http://www.hellanzb.com/trac/") status and display it in a little window (when the applet is clicked). I don't intend to do GUI for hellanzb. From hellanzb homepage you will see that good one already exist. I just want something that give me the status of hellanzb on one click.

For the moment, it is only text-based. Once I sorted all the issues, I am planning on add some icons, colours ...
In order to do so, I will appreciate if some of you guys could get ghellanzb and test it on your station.

You can get it here :[ghellanzb-0.1a]("http://nicoworkspace.free.fr/?q=node/75")

I hope some of you will be interested, and can give me some feedback.

Thanks in advance for your help...

---

### Post by Vadi on 2008-06-12
Just a tip, you should've linked the files directly on this page ([click]("http://nicoworkspace.free.fr/?q=node/75")).

The .deb installed fine, and the applet shows up in my list of add-able applets, however I can't seem to add it. Nothing happens when I click add.

---

### Post by nico_open on 2008-06-12
Yes, good idea. I just changed the link.

For your problem, try to launch ghellanzb ona terminal :

```
sudo python /usr/bin/ghellanzb_applet.py
```
And then try to add the applet.

If it does not work, reset both gnome-panel and bonobo servers:

```
killall gnome-panel
killall bonobo-activation-server
```

---

### Post by Vadi on 2008-06-12
I started the factory, then clicked add. Nothing happened, but some window did show up in AWN and quit right away.

---

### Post by nico_open on 2008-06-13
Just to be sure... Do you have hellanzb up and running.
Is the XMLRPC server is enable and configure with tcp port 8760. Do you use the default password.

Check the following within the hellanzb.conf:

```
# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'
```

What does the following command returns, when yoy try to add the applet to the panel :

```
sudo python /usr/bin/ghellanzb_applet.py
```

---

### Post by Vadi on 2008-06-13
Oh, I don't have the hellanzb thing itself. I think it's a paid subscription service, yeah?

Anyhow you should still do better error detection and let the user know that they don't have it open.

---

### Post by nico_open on 2008-06-13
Regarding hellanzb, it is a newsgroup grabber (and many more things). In order to use it, you need an access to the newsgroups, or through your Internet provider (it is my case), or through a subcription to one of the many newsgroup access websites. 

Sorry for the bug/errors detection. I still have to work on a hellanzb status check and display a result. For me it was so obvious that hellanzb should be up and running that I forgot actually express it and includ checks in the code.

Thanks for your feedback.

---

### Post by Vadi on 2008-06-13
You're welcome, hope you can get a hellanzb user to test this too.

---

