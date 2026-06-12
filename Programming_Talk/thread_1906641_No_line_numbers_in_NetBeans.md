---
title: "No line numbers in NetBeans"
date: 2012-01-09
forum: Programming Talk
---

### Post by gesti on 2012-01-09
Hey guys,
Hope someone can help for me as this fault starts to really annoy me:
NetBeans won't show the line numbers even though the Show Line Numbers is enabled in the View menu.
thx in advance,
gesti

PS. I use Ubuntu 11.10 and NetBeans 7.0.1

---

### Post by dazman19 on 2012-01-09
perhaps try updating the IDE.

I am running 11.10 and netbeans 7.0.1 this instant, and i just went view show line numbers and they dissappeared, then i turned them back on the same way. you can also right click on where they are meant to be and click show line numbers.

The only difference is that I initially installed this machine as 11.04 then installed netbeans 7.0.0 and upgraded both netbeans and 11.10. but i have no problems.

Product Version: NetBeans IDE 7.0.1 (Build 201107282000)
Java: 1.6.0_23; OpenJDK 64-Bit Server VM 20.0-b11
System: Linux version 3.0.0-12-generic running on amd64; UTF-8; en_NZ (nb)
Userdir: /home/daryl/.netbeans/7.0

---

### Post by gesti on 2012-01-10
Well the upgrade to NB 7.1 didn't help. Couldn't turn the line number on neither from the View/**Show line number** nor from right clicking where the number meant to be and tick in the local menu the Show line numbers. Now thinking about this the upgrade didn't help 'cos I imported the old NB's settings.
I had them on for some time, but then I think when I **installed** the **jVi plug-in** (this gives you loads of vim/vi goodies in the editor) was the time when they disappeared.
So I started to poke around in the configuration files of NB and finally found the setting that turned the line number back on:
in this config file: **~/.netbeans/7.1/config/Editors/text/x-php5/Preferences/org-netbeans-modules-editor-settings-CustomPreferences.xml** (this gives the preferences for the editor when editing PHP files)
There I had these lines:
```
    <entry javaType="java.lang.Boolean" name="line-number-visible" xml:space="preserve">
        <value><![CDATA[false]]></value>
    </entry>
```so by** removing this entry** from the file finally gave back the control over the Show/Hide line numbers in the IDE. :mrgreen:
Only their disappearance showed me how important are the line numbers :D hurray for line numbers! \\:D/
PS. uninstalling the jVi plug-in didn't help, as it left the settings behind...

---

### Post by gesti on 2012-03-13
Now, just if someone would find this thread again here is the correct solution:
[http://netbeans.org/bugzilla/show_bug.cgi?id=207662#c4](http://netbeans.org/bugzilla/show_bug.cgi?id=207662#c4)
In menu to set it to default:
Tools / Options / jVi Config -> General -> 'number' 'nu' <-- [tick this]

---

