---
title: "&quot;java&quot; =! &quot;java&quot;"
date: 2007-10-04
forum: Programming Talk
---

### Post by qubodup on 2007-10-04
This may be not the correct subforum, but I'm sure you know the solution to my problem:

I want to use the Sun Java RE, but it appears, that I have to uninstall some JRE-wannabes befor "java" = "java" (Sun's JavaRE)

How can I explicitly run the Sun JRE and not some not-working but open source solution?

And how can I found out weather "java" is Sun's Java? The manpage is confusing and indicates, that "java" is just a link, but a link to what?

I hope you find this not as confusing as I do and can tell me how to use Sun's JRE.

Regards, qubodup

---

### Post by kebes on 2007-10-04
I believe what you want is "[sun-java6-jre]("http://packages.ubuntu.com/feisty/libs/sun-java6-jre")". You'll need to enable the "multiverse" repository, and then just install "sun-java6-jre". You can do this graphically via the package manager (Add/Remove or Synaptic) or on the command line:
```

sudo aptitude install sun-java6-jre

```

---

### Post by qubodup on 2007-10-04
thanks for the reply kebes - I was told what I was looking for,

```
update-alternatives --config java
```

allows me to select which of the javas will be selected via 'java'

---

### Post by Ramses de Norre on 2007-10-04
**sudo update-java-alternatives -l** will show all installed, java providing packages. Use **sudo update-java-alternatives -s *version*** to set the one you want.

---

