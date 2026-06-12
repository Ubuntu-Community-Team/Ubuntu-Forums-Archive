---
title: "Sharing folders with a mac"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by UncleMonty on 2014-12-01
I'm using ubuntu 14.04 and am attempting to share folders with a mac running mavericks. What options do I have please?

(I've installed samba but can't seem to get to grips with it).

---

### Post by Morbius1 on 2014-12-01
Well, let's do a test:

Open Nautilus
Right click your Public folder
Select Local Network Share
Check "Share This Folder" And "Guest Access"
Then select "Create Share"
You just created a read only samba share ( a writeable share takes a bit of work to avoid a permissions night mare between these two systems ).

Now In Finder on OSX the Ubunru server should show up automatically under "Shared"

If it doesn't then create an avahi ( the Linux version of Bonjour on OSX ) service file:
```
gksu gedit /etc/avahi/services/samba.service
```
And copy the following into it:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">SMB %h</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
[COLOR=#0000cd]* The tricky part here is that the first line must not have any leading spaces in it or else it won't be recognized as a service file. You know you did it right when you save the file since it will change colors:*[/COLOR]
[ATTACH=CONFIG]258310[/ATTACH]
Now in Finder it should show up under "Shared" as "SMB *ubuntu-host-name*"

[COLOR=#0000cd] **EDIT**: I should have mentioned that avahi has two requirements:[/COLOR]
*** Port 5353 must be open.
*** Avahi must be running  --- it should be running automatically:
```
sudo service avahi-daemon start
```

---

