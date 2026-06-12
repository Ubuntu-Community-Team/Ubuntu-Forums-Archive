---
title: "[SOLVED] [GCC Problem]  Localized output - How to get rid of it :)  ?"
date: 2008-11-10
forum: Programming Talk
---

### Post by dempl_dempl on 2008-11-10
Hi  folks, 

 To show what I mean , here  are couple of simple examples:
   
```

dule@dule-laptop:~$ gcc --version
gcc (&#1043;&#1062;&#1062;) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright © 2006 Free Software Foundation, Inc.
&#1054;&#1074;&#1086; &#1112;&#1077; &#1089;&#1083;&#1086;&#1073;&#1086;&#1076;&#1072;&#1085; &#1089;&#1086;&#1092;&#1090;&#1074;&#1077;&#1088;; &#1087;&#1086;&#1075;&#1083;&#1077;&#1076;&#1072;&#1112;&#1090;&#1077; &#1080;&#1079;&#1074;&#1086;&#1088;&#1077; &#1079;&#1072; &#1091;&#1089;&#1083;&#1086;&#1074;&#1077; &#1082;&#1086;&#1087;&#1080;&#1088;&#1072;&#1114;&#1072;. &#1053;&#1077;&#1084;&#1072; &#1041;&#1048;&#1051;&#1054; &#1050;&#1040;&#1050;&#1042;&#1045;
&#1043;&#1040;&#1056;&#1040;&#1053;&#1062;&#1048;&#1032;&#1045;; &#1095;&#1072;&#1082; &#1085;&#1080; &#1079;&#1072; &#1050;&#1054;&#1052;&#1045;&#1056;&#1062;&#1048;&#1032;&#1040;&#1051;&#1053;&#1059; &#1042;&#1056;&#1045;&#1044;&#1053;&#1054;&#1057;&#1058; &#1080;&#1083;&#1080; &#1048;&#1057;&#1055;&#1059;&#1034;&#1040;&#1042;&#1040;&#1034;&#1045; &#1054;&#1044;&#1056;&#1045;&#1026;&#1045;&#1053;&#1045; &#1055;&#1054;&#1058;&#1056;&#1045;&#1041;&#1045;.

```

```

dule@dule-laptop:~$ gcc
gcc: &#1085;&#1077;&#1084;&#1072; &#1091;&#1083;&#1072;&#1079;&#1085;&#1080;&#1093; &#1076;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1072;

```

Ok, I admit , it looked cool couple of months ago   . I still like GCC showing errors on Serbian. Although, translations are sometimes funny :)

The problem is, however, that now I'm having problem with my editor ( SlickEdit )  . It can't parse the GCC's build output right ( obviously some Unicode issue with SlickEdit ) . The thing is, 

The thing is, I really forgot how on Earth did I installed that :)  .

I would be grateful if someone could tell me any way to display error messages in English . 

I will even remove Serbian completely, if necessary , but , it would be a lot better if gcc had something like  '--force-us-english-output' option :)  .


What I've tried so far :
[LIST]
[*]Set English to be default KDE's language
[*]Remove localization package for GCC
[/LIST] 

And, I almost forgot , Ubuntu is 7.10 , GCC is 4.1  .


Thanks in advance,
Eh, Me :)

---

### Post by geirha on 2008-11-10
```
LANG= gcc --version
# Or a specific language
LANG=en_US.UTF8 gcc --version
# You can also export it to change translations for
# all commands run in that terminal
export LANG=en_US.UTF8
gcc --version
# And this lists all locales you have available. 
# LANG= is the same as LANG=C
locale -a

```

---

### Post by dempl_dempl on 2008-11-10
Thanks mate, problem solved :)

---

