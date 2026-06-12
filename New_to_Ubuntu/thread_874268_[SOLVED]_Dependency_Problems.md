---
title: "[SOLVED] Dependency Problems"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-29
OK, I just did a complete reinstall, and after updating, got a message saying not all the updates were successful. There was a pop-up with the following script:

> E: gnome-applets-data: subprocess post-installation script returned error exit status 134
E: gnome-applets: dependency problems - leaving unconfigured

Any idea what this means?

---

### Post by Pro-reason on 2008-07-29
It's an Ubuntu screw-up.  Let's see if we can fix it.

Do this in a terminal:

```

sudo dpkg --force-all --remove gnome-applets-data gnome-applets
sudo apt-get update ; sudo apt-get --fix-broken install

```

Tell me if it works.

---

### Post by mczonie on 2008-07-29
> **Pro-reason said:**
> It's an Ubuntu screw-up.  Let's see if we can fix it.

Do this in a terminal:

```

sudo dpkg --force-all --remove gnome-applets-data gnome-applets
sudo apt-get update ; sudo apt-get --fix-broken install

```

Tell me if it works.

After I entered that in the terminal, this happened:

butes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">
  ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : error parsing attribute name
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : attributes construct error
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1458: parser error : Couldn't find end of Start Tag tocsed line 1458
<tocsed="gnome-terminal-reset">&#1053;&#1072;&#1083;&#1072;&#1075;&#1086;&#1076;&#1078;&#1077;&#1085;&#1085;&#1103; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
       ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1459: parser error : Opening and ending tag mismatch: tocsect1 line 1451 and tocsect2
</tocsect2>
           ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1460: parser error : expected '>'
</tocsect1>
     ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: doc line 1416 and toc
</toc></doc></sect>
      ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1475: parser error : Opening and ending tag mismatch: sect line 1331 and doc
</toc></doc></sect>
            ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1932: parser error : Opening and ending tag mismatch: ScrollKeeperContentsList line 2 and sect
  </sect>
         ^
/var/lib/scrollkeeper/uk/scrollkeeper_extended_cl.xml:1934: parser error : Extra content at the end of the document
  <sect categorycode="KDE">

---

### Post by Pro-reason on 2008-07-29
> **mczonie said:**
> After I entered that in the terminal, this happened:
That's really weird.  I don't see how that could be caused by the commands I gave.  Can you tell at what point that happened?  Was it when the packages were removed, or when we tried to fix the dependencies?

Can you confirm what desktop environment (GNOME, KDE...) you intend to mainly use?

---

### Post by mczonie on 2008-07-29
*That's really weird.  I don't see how that could be caused by the commands I gave.  Can you tell at what point that happened?  *

It was when I entered the code you gave me. That's what came up in the terminal.

Now there's some weird little icon on the toolbar where the update icon is usually displayed. It's a red circle with a white horizontal bar in it. I clicked it, and it showed the two gnome updates, but when I tried to install them, it told me I have one broken package on my system and to use the "broken" filter to locate it.

I noticed that there's some Russian words in there. You think someone has hacked my computer? I don't know how that would be even possible, since this is a brand new reinstall.

*Can you confirm what desktop environment (GNOME, KDE...) you intend to mainly use?*

I'm brand new to this. I don't even know what a GNOME or KDE is.

---

### Post by Pro-reason on 2008-07-29
> **mczonie said:**
> *That's really weird.  I don't see how that could be caused by the commands I gave.  Can you tell at what point that happened?  *

It was when I entered the code you gave me. That's what came up in the terminal.[/code]
Yes, you said that before.

But when exactly?  I gave three commands.  You would have had to press enter after the first command.  Did the output happen then?  After that, you would have had to paste the second line, on which I had given you two commands joined by a semicolon.  They would have executed one right after the other, but it still should have been apparent which command gave the output.

> **mczonie said:**
> 
Now there's some weird little icon on the toolbar where the update icon is usually displayed. It's a red circle with a white horizontal bar in it. I clicked it, and it showed the two gnome updates, but when I tried to install them, it told me I have one broken package on my system and to use the "broken" filter to locate it.

Yes, that's some sort of updater.  It could be the Adept updater or similar.  I don't know how your computer is set-up exactly.  Opening an updater will produce an error until the dependency problem is fixed.

> **mczonie said:**
> 
I noticed that there's some Russian words in there. You think someone has hacked my computer? I don't know how that would be even possible, since this is a brand new reinstall.
Oh, I just assumed you were Russian or Ukrainian or something, and had installed it like that.  I can see no reason whatsoever why it should be like that.  What did you install the system from?

> **mczonie said:**
> 
*Can you confirm what desktop environment (GNOME, KDE...) you intend to mainly use?*

I'm brand new to this. I don't even know what a GNOME or KDE is.

The main parts of any Linux system are pretty much the same.  However, the graphical desktop that you do stuff on comes in several varieties.  Ubuntu by default gives you what is called the [GNOME Desktop Environment]("http://en.wikipedia.org/wiki/GNOME").  Sometimes Ubuntu is branded as "Kubuntu", indicating that it uses the [K Desktop Environment]("http://en.wikipedia.org/wiki/KDE") instead.  I myself use Kubuntu.

I ask because the output that you posted mentioned KDE a couple of times.

---

### Post by Pro-reason on 2008-07-29
I have a hunch:

Did you at some point during download or installation choose some option that said "**UK**", thinking that it meant "United Kingdom", when in fact it actually stands for "Ukraine" (GB is the code for Britain)?

---

### Post by mczonie on 2008-07-29
> **Pro-reason said:**
> But when exactly? I gave three commands.

I didn't know they were three separate commands. I entered all three at once. It doesn't matter, anyway. I just did another complete reinstall, and the problem went away. Thanks anyway.

---

