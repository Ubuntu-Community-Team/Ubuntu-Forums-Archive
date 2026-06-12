---
title: "Duplicate file"
date: 2010-02-24
forum: Programming Talk
---

### Post by jdandcocacola on 2010-02-24
[B][I]Hi all,

Was wondering could I get some help, have a piece of code:

[/I][/B]      [FONT=&quot]OUTF=rem-duplicates.sh;[/FONT]
  [FONT=&quot]echo "#! /bin/sh" > $OUTF;[/FONT]
  [FONT=&quot]find "$@" -type f -exec md5sum {} \; |[/FONT]
  [FONT=&quot]    sort --key=1,32 | uniq -w 32 -d --all-repeated=separate |[/FONT]
  [FONT=&quot]    sed -r 's/^[0-9a-f]*( )*//;s/([^a-zA-Z0-9./_-])/\\\1/g;s/(.+)/#rm \1/' >> $OUTF;[/FONT]
  [FONT=&quot]chmod a+x $OUTF; ls -l $OUTF[/FONT]
  
  
This finds duplicate files but how would I go about deleting the files found?

jdandcocacola

---

