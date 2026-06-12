---
title: "Focus problem with pygtk in gnome-panel"
date: 2009-09-26
forum: Programming Talk
---

### Post by aiwarrior on 2009-09-26
Hi all

I am developing a gnome pannel with pygtk for personal use that works like [this]("http://www.angel.net/~nic/passwd.html"). 

**Description:**
[INDENT]A gtk.Entry stands in a panel where a user(me) writes the site name. When enter is pressed the a MD5 hash is generated from concatenations of the master password and the text inserted in the entry box. A base64 encoding is done on that hash and the first 8 characters are set on the same entry box.[/INDENT]

**Problem:** 
[LIST]
[*]The gtk entry box is only focused on startup or when another applet is run and focused (i tried the gnome dictionary panel), resulting in the user being unable to insert any text/set the cursor in the entry box. 
[*]The applet behaves with no problem when debuging with a parent window, allowing input normally.
[/LIST]

**Tried Solutions:**
[LIST]
[*]I have tried grab_focus() to no avail
[*]I have tried making it sensitive
[/LIST]

**To test the code:**
[LIST]
[*]You must change the .server file so as to point to the path of the executable in your system.
[*]Use the attached file
[/LIST]

**Server file**
```
<oaf_info>
	<oaf_server iid="OAFIID:SampleApplet_Factory" 
		    type="exe" 
		    location="/home/pneves/appletxp.py">

		<oaf_attribute name="repo_ids" type="stringv">
			<item value="IDL:Bonobo/GenericFactory:1.0"/>
			<item value="IDL:Bonobo/Unknown:1.0"/>
		</oaf_attribute>
		<oaf_attribute name="name" type="string" value="Sample Applet Factory"/>
		<oaf_attribute name="description" type="string" value="Sample Applet's factory that launches the applet"/>
	</oaf_server>

	<oaf_server iid="OAFIID:SampleApplet" 
		    type="factory" 
		    location="OAFIID:SampleApplet_Factory"> 
		<oaf_attribute name="repo_ids" type="stringv">
			<item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
			<item value="IDL:Bonobo/Control:1.0"/>
			<item value="IDL:Bonobo/Unknown:1.0"/>
		</oaf_attribute>
		<oaf_attribute name="name" type="string" value="Sample Applet"/>
		<oaf_attribute name="description" type="string" value="Sample applet's description"/>
		<oaf_attribute name="panel:category" type="string" value="Utility"/>
		<oaf_attribute name="panel:icon" type="string" value="gnome-laptop.png"/>
	</oaf_server>
</oaf_info>

```

---

### Post by karamfil on 2010-03-11
Hello, 

I have the same problem.
Does anybody know a solution?

Thanks

---

