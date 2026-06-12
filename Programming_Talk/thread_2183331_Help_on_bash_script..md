---
title: "Help on bash script."
date: 2013-10-24
forum: Programming Talk
---

### Post by obscuremind on 2013-10-24
I there iam creating a bash script to pick a string from an xml, and the if the xml as the value runs the rest of the script, but it doesnt validate if the value its the correct one.

Here it is.

```

answer="http://127.0.0.1/web/messageanswer?getanswer=now"


wget -qO - $answer | tee /tmp/answer.xml


chmod 755 /tmp/answer.xml


outputanswer=$(cat /tmp/answer.xml | grep -E -m 1 -o "<e2statetext>(.*)</e2statetext>" /tmp/answer.xml)


answeryes="Answer is YES!"


if [[ "$outputanswer" == *$answeryes* ]];


then

```

the output of answer="http://127.0.0.1/web/messageanswer?getanswer=now" its this:

```

<e2simplexmlresult>
 <e2state>True</e2state>
 <e2statetext>Answer is NO!</e2statetext>
</e2simplexmlresult>

```

or 

```

<e2simplexmlresult>
 <e2state>True</e2state>
 <e2statetext>Answer is YES!</e2statetext>
</e2simplexmlresult>

```

---

### Post by Vaphell on 2013-10-24
why do you make the xml file executable? read=4, write=2, exec=1 so 7=rwx, 5=rx

also *cat* is unnecessary given you pass the file to grep directly.

if you check for pattern with wildcards you can't use strict comparison ==, you need =~
```
$ outans=$( echo '<>Answer is YES!<>' )
$ ans='Answer is YES!'
$ [[ $outans =~ .*$ans.* ]] && echo TRUE
TRUE
$ ans_regex='.*Answer is YES!.*'
$ [[ $outans =~ $ans_regex ]] && echo TRUE
TRUE
```

you can also strip the line from the xml tags
```
$ outans=$( echo '<>Answer is YES!<>' )
$ outans=${outans#*>}; outans=${outans%<*}
$ echo $outans
Answer is YES!
```
and then regex won't be necessary so plain == will do.

---

### Post by obscuremind on 2013-10-24
```


ans="http://127.0.0.1/web/messageanswer?getanswer=now"


wget -qO - "$ans" | tee /tmp/answer.xml


outans=$(grep -E -m 1 -o "<e2statetext>(.*)</e2statetext>" /tmp/answer.xml)


outans=${outans#*>}; outans=${outans%<*}


if [ "$outans" == "Answer is YES!" ];


then

```
 
well this is the changes i made with your help, everything outputs fine, but when it runs the if, it allways says that the $outans is equal to "Answer is YES!" even if its not, and runs the script instead of giving the error.

what could be wrong?

---

### Post by Vaphell on 2013-10-24
do you print out what you have in $outans for debug purposes?

---

### Post by obscuremind on 2013-10-25
Yes i did, that part its working its bad coding of me >.<

---

