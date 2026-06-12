---
title: "Blender 2.69"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by bcicenas on 2014-01-12
I've got this when i tried to run blender 2.69
root@bt:~# ./.blender/blender
[COLOR=#008000][SIZE=4]connect failed: No such file or directory <------ but there is blender in that directory[/SIZE][/COLOR]     why is that?
AL lib: UpdateDeviceParams: Failed to set 44100hz, got 48000hz instead
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  42
  Current serial number in output stream:  42

---

### Post by mcduck on 2014-01-13
First question wwould be why are you trying to run it as root? 

Anyway, your command is looking for the .blender directory inside root's home directory, (once again a bit strabge place for an app that doesn't require running as root). I'd recommend just extracting Blender into your normal user's home directory and then making sure you actually cd into the correct directory before running "./blender".

---

### Post by Impavidus on 2014-01-13
+1 to mcduck: in general it's a bad idea to run such programs as root. Blender 2.62 is in the 12.04 repositories, later releases may have later versions. Even when you decide you need to manually install 2.69, best not to do so in root's home directory.

Actually, if the file **./.blender/blender** didn't exist I'd expect the error **bash: ./.blender/blender: No such file or directory**. The error may be generated further downstream.

---

### Post by monkeybrain20122 on 2014-01-13
To run blender simply download it from blender.org , extract, open the folder and click on blender and that's it. No need for command line and definitely not need to be root (in general becoming root is a  bad idea, if you need root privilege to run a command,--not in this instance definitely,--just use sudo)

---

