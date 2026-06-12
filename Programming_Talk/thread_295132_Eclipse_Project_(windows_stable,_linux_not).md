---
title: "Eclipse Project (windows stable, linux not)"
date: 2006-11-07
forum: Programming Talk
---

### Post by mad0master on 2006-11-07
Well, after getting eclipse (i've just downloaded archive files and unziped them) i try to use my Win-eclipse-made project. But it tells me, that it contains lots of errors! :confused: 

Just see some of them:

[LIST]
[*]Incompatible operand types Character and char
[*]Syntax error on token "enum", class expected
[*]Syntax error, 'for each' statements are only available if source level is 5.0
[*]The method format(Locale, String, Object[]) in the type PrintStream is not applicable for the arguments (String, String, String, String, String)	
[*]The type Collection is not generic; it cannot be parameterized with arguments <String>
[/LIST]

and even more...

Where is the problem?

---

### Post by Ziggurat on 2006-11-07
I never have problems like this. I use eclipse on both Win and Ubuntu. The one problem i can tell you is that eclipse is terrible much slower on linux.

For the things you are telling me i can guess some of this may bve wrong:

[LIST]
[*]Are you using Java 1.5?
[*]If true, do you have eclipse configured (on linux) for java 1.5?[/LIST]I think you have different compiler options enabled on linux.

Hope it helps.

---

### Post by hod139 on 2006-11-07
See this howto for setting up java 1.5 and the repository version of eclipse.  [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
You should be able to get java 1.5 working and eclipse (even if you don't use the repo version) faster using the howto.

---

### Post by mad0master on 2006-11-08
Yep, i've installed sun-java-1.5.0.
In eclipse options i've set it to use java from /usr/lib/jvm/sun-java-1.5.08

Well, i'll try to install eclipse from reposyitory!

---

### Post by Ramses de Norre on 2006-11-08
Have you also set the jre in eclipse to sun-java?

---

### Post by mad0master on 2006-11-13
Thnx guys, i've set jre in eclipse, cleaned the proj and was very pleased! Never panic! ;-)

---

