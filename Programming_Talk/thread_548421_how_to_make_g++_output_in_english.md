---
title: "how to make g++ output in english?"
date: 2007-09-11
forum: Programming Talk
---

### Post by vexorian on 2007-09-11
I use a little Java program that reads output from a compiler and shows it, the problem is that it is made to only support english since other languages get encoding issues,

The ought to be a way to change g++'s out put language using language packs or something, if not is there at least a way to enforce an encoding?

---

### Post by engla on 2007-09-11
Set environment variables before you run a subprocess. Normally setting 'LANG' to 'C' works and turns off localization.

---

### Post by aks44 on 2007-09-11
Those bash functions should work (I use them in some scripts that need to parse outputs):

```
backupLanguageAndSwitchToEnglish()
{
	SCRIPT_BACKUP_LANG=$LANG
	SCRIPT_BACKUP_LC_ALL=$LC_ALL
	LANG=US
	LC_ALL=US
	export LANG
	export LC_ALL
}

restoreOriginalLanguage()
{
	LANG=$SCRIPT_BACKUP_LANG
	LC_ALL=$SCRIPT_BACKUP_LC_ALL
	export LANG
	export LC_ALL
}
```


Well, I know that technically it switches to American, not to English, but let's not start a debate over that huh? :p

---

### Post by vexorian on 2007-09-11
All right , thanks.

Edit ; The knowledge provided has been succesfuly used. I actually made me a usg++.sh that temporarily changes the language  and runs g++, thanks

---

