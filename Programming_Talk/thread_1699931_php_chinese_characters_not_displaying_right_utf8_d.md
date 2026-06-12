---
title: "php chinese characters not displaying right utf8 data"
date: 2011-03-04
forum: Programming Talk
---

### Post by sdowney717 on 2011-03-04
I am writing this app for getting utf8 data from the Library of Congress.
If I save the data string into a file and open it, the chinese is correct.
If I display it in a browser window, the chinese is not working as is anything different except for english ansi.

screenshot shows the difference.
So, how to make it show up correctly?

I may have solved it with this here put at top of php script

<meta http-equiv="content-type" content="text/html; charset=UTF-8">

---

### Post by sdowney717 on 2011-03-04
this is how they look now running in the PHP browser script
just a test to see if the chars show up here
so I think it is working
```
=LDR 02210cam a22004334a 4500
=001 15400882
=005 20090516163507.0
=008 080729s2006 cc b 000 0 chi
=906 __$a7$bcbc$corignew$d3$encip$f20$gy-nonroman
=925 0_$aacquire$b1 shelf copy$xpolicy default
=955 __$aCNP to LC 2008-08-08$icc17 2009-05-16$ecc17 2009-05-16 to BCCD
=010 __$a 2008404590
=020 __$a781112243X
=020 __$a9787811122435
=035 __$a(OCoLC)ocn236486484
=040 __$aDLC$cDLC$dDLC
=050 00$aDS796.K8$bA16 2006
=066 __$c$1
=245 00$6880-01$a2005 : Li shi de hui huang :$bji nian Kunming jian cheng 1240 zhou nian, Zheng He xia xi yang 600 zhou nian, hu guo yun dong 90 zhou nian /$cKunming Shi she hui ke xue jie lian he hui, Yunnan Sheng Zhongguo jin dai shi yan jiu hui bian.
=880 00$6245-01/$1$a2005 : &#21382;&#21490;&#30340;&#36745;&#29004;:$b&#32426;&#24565;&#26118;&#26126;&#24314;&#22478;1240&#21608;&#24180;, &#37073;&#21644;&#19979;&#35199;&#27915;600&#21608;&#24180;, &#25252;&#22269;&#36816;&#21160;90&#21608;&#24180; /$c&#26118;&#26126;&#24066;&#31038;&#20250;&#31185;&#23398;&#30028;&#32852;&#21512;&#20250;, &#20113;&#21335;&#30465;&#20013;&#22269;&#36817;&#20195;&#21490;&#30740;&#31350;&#20250;&#32534;.
=246 30$6880-02$aLi shi de hui huang ;$bji nian Kunming jian cheng 1240 zhou nian, Zheng He xia xi yang 600 zhou nian, hu guo yun dong 90 zhou nian
=880 30$6246-02/$1$a: &#21382;&#21490;&#30340;&#36745;&#29004;:$b&#32426;&#24565;&#26118;&#26126;&#24314;&#22478;1240&#21608;&#24180;, &#37073;&#21644;&#19979;&#35199;&#27915;600&#21608;&#24180;, &#25252;&#22269;&#36816;&#21160;90&#21608;&#24180;
=246 1_$iRunning title also in pinyin :$a2005 : Lishi de huihuang
=250 __$6880-03$aDi 1 ban.
=880 __$6250-03/$1$a&#31532;1&#29256;.
=260 __$6880-04$aKunming Shi :$bYunnan da xue chu ban she,$c2006.
=880 __$6260-04/$1$a&#26118;&#26126;&#24066; :$b&#20113;&#21335;&#22823;&#23398;&#20986;&#29256;&#31038;,$c2006.
=300 __$a2, 3, 382 p. ;$c24 cm.
=651 _0$aChina$xHistory$yRevolution, 1915-1916.
=651 _0$6880-05$aKunming Shi (China)$xHistory.
=880 _4$6651-05/$1$a&#26118;&#26126;&#24066; (China)$xHistory.
=610 20$6880-06$aZheng He,$d1371-1435$xTravel.
=880 24$6610-06/$1$a&#37073;&#21644;,$d1371-1435$xTravel.
=710 2_$6880-07$aKunming Shi she hui ke xue jie lian he hui.
=880 2_$6710-07/$1$a&#26118;&#26126;&#24066;&#31038;&#20250;&#31185;&#23398;&#30028;&#32852;&#21512;&#20250;.
=710 2_$6880-08$aYunnan Sheng Zhongguo jin dai shi yan jiu hui.
=880 2_$6710-08/$1$a&#20113;&#21335;&#30465;&#20013;&#22269;&#36817;&#20195;&#21490;&#30740;&#31350;&#20250;.
=923 __$d20080728$nT200800994$sCNP
=985 __$aCNP load$d2008-08-08

```

---

