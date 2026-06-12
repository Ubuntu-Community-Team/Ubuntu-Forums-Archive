---
title: "Some Help in Awk"
date: 2008-06-12
forum: Programming Talk
---

### Post by umshiva on 2008-06-12
Hi Buddies,

cn.rep:REP008 MTH  30/05/2008-22:08:21 RETRY.... 2
cn.rep:REP030 MTH  30/05/2008-22:17:20 RETRY.... 2

My program is ...

cut -f 1,2 -d ":"  rep_temp > temp_retr
cat temp_retr | while read line
   do
      echo $line  >> extract_retry
   done
 sed '$s/...$//g'  extract_retry >temp_retry
 sed 's/:/ /g ' temp_retry > temp1_retry

My output is 

cn.report REP008 MTH 20080530 30/05/2008-22
cn.report REP030 MTH 20080530 30/05/2008

I need  to have 

cn.report REP008 MTH 20080530 30/05/2008
cn.report REP030 MTH 20080530 30/05/2008

as output 

and morover i need to generate other file 

which will have 

 REP008    20080530 -- RETRY ENTRY 
 REP030    20080530 -- RETRY ENTRY

NO OF RETRY ENTRIES : 2

CAn any one help me with this ..... 

Thanks in advance

---

### Post by ghostdog74 on 2008-06-12
if your data has a fixed format like that:
```

awk 'BEGIN{FS="-"}
{
 print "before: $1: "$1
 gsub("rep","report",$1)
 gsub(":"," ",$1)  
 m=split($1,a," ")
 n=split(a[m],b,"/") 
 newdate=b[3]b[2]b[1] 
 print a[1],a[2],a[3],newdate,a[m]
}
' file

```
output
```

# ./test.sh
before: $1: cn.rep:REP008 MTH 30/05/2008
cn.report REP008 MTH 20080530 30/05/2008
before: $1: cn.rep:REP030 MTH 30/05/2008
cn.report REP030 MTH 20080530 30/05/2008


```

---

### Post by HalPomeranz on 2008-06-12
> **umshiva said:**
> 
I need  to have 

cn.report REP008 MTH 20080530 30/05/2008
cn.report REP030 MTH 20080530 30/05/2008


```

awk -F'(:| |/|-)' '{ print $1 "ort " $2 " " $3 " " $6 $5 $4 " " $4 "/" $5 "/" $6 }' inputfile

```

> **umshiva said:**
> 
and morover i need to generate other file which will have 

 REP008    20080530 -- RETRY ENTRY 
 REP030    20080530 -- RETRY ENTRY

NO OF RETRY ENTRIES : 2


```

awk -F'(:| |/|-)' '/RETRY/ { tot += 1; print $2 "\t" $6 $5 $4 " -- RETRY ENTRY" }
                   END { print ""; print "NO OF RETRY ENTRIES : " tot }' inputfile

```

---

### Post by umshiva on 2008-06-12
Hi Pal,

awk 'BEGIN{FS="-"}
{
 print "before: $1: "$1
 gsub("rep","report",$1)
 gsub(":"," ",$1)
 m=split($1,a," ")
 n=split(a[m],b,"/")
 newdate=b[3]b[2]b[1]
 print a[1],a[2],a[3],newdate,a[m]
}
' rep_temp

ksh: syntax error: `'' unmatched

cat rep_temp

ckaur@PROD /home/ckaur/shiva/script_dead_07_06> cat rep_temp
cn.rep:REP008 MTH 30/05/2008-22:08:21 RETRY.... 2
cn.rep:REP030 MTH 30/05/2008-22:17:20 RETRY.... 2


Please help

Thanks in advance

---

### Post by umshiva on 2008-06-12
Sorry , both of your genius code worked , i made the mistake 

Thanks a bunch

---

