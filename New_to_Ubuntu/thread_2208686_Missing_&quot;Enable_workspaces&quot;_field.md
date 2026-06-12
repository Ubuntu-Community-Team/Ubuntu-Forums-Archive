---
title: "Missing &quot;Enable workspaces&quot; field"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by 700 on 2014-03-01
Hi,
On my Ubuntu 12.04.4 LTS after last update I'm not only missing workspaces - I'm missing also "[Enable workspaces]("http://i.stack.imgur.com/wQ3hD.png")" field from the System Settings... > Appearance > Behaviour (tab).
How to get my workspaces back, plz?

---

### Post by deadflowr on 2014-03-01
There is no "Enable Workspaces" in 12.04.
Never was, and never going to be...

That said, do you have any tweak tools installed?
Something like ccsm or ubuntu tweak, or MyUnity.

If so, you can add or subtract workspaces using those.

---

### Post by 700 on 2014-03-01
I'm using CCSM (CompizConfig Settings Manager), but this function stopped working after last Ubuntu update.

---

### Post by deadflowr on 2014-03-01
Can you not re-enable the settings by going to ccsm > General Options > Desktop Size and setting the workspaces.
12.04 should be set default with 2 horizontal and 2 vertical.

---

### Post by 700 on 2014-03-01
CCSM is not reacting on any changes there.

---

### Post by steeldriver on 2014-03-01
How about

```
gsettings reset org.gnome.desktop.wm.preferences num-workspaces
```

or

```
gsettings set org.gnome.desktop.wm.preferences num-workspaces 4
```

---

### Post by deadflowr on 2014-03-01
You're not logging into unity-2d, are you?

Or somehow unity-2d is being default to?

If you are booting into unity-2d, then nothing with ccsm would help, because unity-2d uses metacity and not compiz.

Do you know what updates you got?
Maybe an update for xorg or a driver update.

---

### Post by 700 on 2014-03-05
Terminal reply:
> No such schema 'org.gnome.desktop.wm.preferences'

---

### Post by 700 on 2014-03-05
> You're not logging into unity-2d, are you?
I'm not logging anywhere.

> Do you know what updates you got?
I've got only all suggested updates from Update Manager. There's nothing else there.

---

### Post by deadflowr on 2014-03-05
Do you have auto-login set, then?

We can see if you're logging into unity or unity-2d by running these
```
/usr/lib/nux/unity_support_test -p
```
this command will see if the settings of the system are able to run unity.
Sometimes a driver change might cause the system not to be able to run unity correctly.
```
echo $DESKTOP_SESSION
```
If it says ubuntu, you are running full unity.
If it says ubuntu2d, then that is unity-2d.

---

### Post by 700 on 2014-03-20
```
/usr/lib/nux/unity_support_test -p
```
Returns:> 
Major opcode of failed request: 153 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 22
Current serial number in output stream: 22
```
echo $DESKTOP_SESSION
```
Returns:
> ubuntu-2d

---

### Post by steeldriver on 2014-03-20
That's really odd - I'm also using 12.04 with ubuntu-2d and the gsettings method works for me

Can you check you have the schema package installed and the schema files in place?

```

dpkg -l gsettings-desktop-schemas

find /usr/share/ -name '*.wm.*' 2>/dev/null

```

---

### Post by deadflowr on 2014-03-20
From the error output, it looks like what others get with a botched flgrx driver install/update
Even though this is marked as a duplicate in ask ubuntu, it does provide basic links on the fix.
[http://askubuntu.com/questions/175744/x-error-of-failed-request-badrequest-invalid-request-code-or-no-such-operation](http://askubuntu.com/questions/175744/x-error-of-failed-request-badrequest-invalid-request-code-or-no-such-operation)

This, of course, is total speculation on my part, as I don't know if you have an amd/ati gpu or not.

---

