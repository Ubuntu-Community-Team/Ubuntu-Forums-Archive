---
title: "problem with sed in script"
date: 2010-06-01
forum: Programming Talk
---

### Post by supererki on 2010-06-01
hello : 
in the script there is a sed command : 

sed -e 's/\/\\\\/g; s///\\//g; s/:::.*//g'
anyway, it doesn't work :

sed: -e expression #1, char 15: unknown option to `s'

any help would be apprechiated.
The whole script goes like :

#!/usr/bin/env bash

sed -e 's/\/\\\\/g; s///\\//g; s/:::.*//g' All_attack.txt > All_attack.txt~

n=0
for i in `ls -1 *.xml`
do
        while read line
        do
                sed "s/?/${line}/" $i > $i.$n
                echo "Writing $i.$n"
                echo -n "."
                let "n+=1"
        done < All_attack.txt~
        let n=0
done
rm All_attack.txt~

exit 0
---------

attack file is something like : (small part)
%27%20or%201=1:::SQL Injection (SQLi)
%20$(sleep%2050):::SQL Injection (SQLi)
%20'sleep%2050':::SQL Injection (SQLi)
char%4039%41%2b%40SELECT:::SQL Injection (SQLi)
&apos;%20OR:::SQL Injection (SQLi)
'sqlattempt1:::SQL Injection (SQLi)
(sqlattempt2):::SQL Injection (SQLi)
|:::LDAP Injection
%7C:::LDAP Injection
*|:::LDAP Injection
%2A%7C:::LDAP Injection
*(|(mail=*)):::LDAP Injection
%2A%28%7C%28mail%3D%2A%29%29:::LDAP Injection
*(|(objectclass=*)):::LDAP Injection
%2A%28%7C%28objectclass%3D%2A%29%29:::LDAP Injection
(:::LDAP Injection
%28:::LDAP Injection
):::LDAP Injection
%29:::LDAP Injection
&:::LDAP Injection
%26:::LDAP Injection
!:::LDAP Injection
%21:::LDAP Injection
/:::LDAP Injection
//:::LDAP Injection
//*:::LDAP Injection
*/*:::LDAP Injection
@*:::LDAP Injection
x' or name()='username' or 'x'='y:::LDAP Injection
count(/child::node()):::XPath Injection
<![CDATA[<script>var n=0;while(true){n++;}</script>]]>:::Script Injection
<name>','')); phpinfo(); exit;/*</name>:::Script Injection

it is not anything malicious, its for fuzztesting my own webservice.

---

### Post by shel-hall on 2010-06-01
> **supererki said:**
> hello : 
in the script there is a sed command : 

sed -e 's/\/\\\\/g; s///\\//g; s/:::.*//g'
anyway, it doesn't work :

sed: -e expression #1, char 15: unknown option to `s'
That's not the way to have multiple commands in sed.

Try ...
```

sed -e 's/\/\\\\/g' -e 's///\\//g' -e 's/:::.*//g'

```
... which I don't guarantee will do what you want, but I think it is the correct use of the -e option for multiple commands.

Rather than using all those backslash escapes, you might want to look into using a different delimiter in the 's' commands.

-Shel

---

### Post by DaithiF on 2010-06-01
its fine to separate multiple search/replaces with a ';' in sed.  The problem is with your second expression:

**s///**\\//g;

the part I've bolded is the search/replace instruction, the remainder is not recognised by sed and hence the error.  I'm not sure what exactly you're trying to search replace here ... some number of forward slashes I guess, but either escape the each / with a preceding \, or else do as Shel suggested and use a different delimiter, e.g.:
s#///##g

---

### Post by supererki on 2010-06-01
I have empty SOAP requests, which i extracted from soapUI > 
The script is supposed to loop through each line in WSFuzzer’s Attack_all.txt and replace every placeholder parameter in each XML file with the attack string
It should generate one XML file for each attack string per method

Request example: 

<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:GetAddressComponentListUpdatesByLevelAndParent>
         <!--Optional:-->
         <tem:level>?</tem:level>
         <!--Optional:-->
         <tem:parentId>?</tem:parentId>
         <!--Optional:-->
         <tem:lastRequest>?</tem:lastRequest>
      </tem:GetAddressComponentListUpdatesByLevelAndParent>
   </soapenv:Body>
</soapenv:Envelope>


all_attack is here : [http://www.neurofuzz.com/modules/software/wsfuzzer/All_attack.txt](http://www.neurofuzz.com/modules/software/wsfuzzer/All_attack.txt)

---

### Post by DaithiF on 2010-06-01
i don't think sed is the right tool for the job.

because you're using sed to create a value that you then use in another sed expression you would need to double escape all the slashes.

I would suggest you use something else to do the replacing, to avoid the escaping madness, e.g. python.

Having said that, this may be what you want:
sed 's#\\#\\\\\\\\#g;s#/#\\\\/#g;s/:::.*//g' All_attack.txt > All_attack.txt~

and then use:
sed "s#?#${line}#" $i > $i.$n  in your loop

---

### Post by supererki on 2010-06-01
Oh!

thank you very much! that did the trick!
super
Thanks!

---

### Post by supererki on 2010-06-01
one more thing, since you have already put some time into the problem :
the thing is that the request is like :
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:AsutusHasAmetnikWithPrivilege>
         <!--Optional:-->
         <tem:asutusId>?</tem:asutusId>
         <!--Optional:-->
(skipped...)

It begins with <?xml ... is it possible to exclude the first line somehow with sed command?

---

### Post by supererki on 2010-06-02
solved :

sed "s/>?</>${line}</" $i > $i.$n
instead of 
sed "s#?#${line}#" $i > $i.$n

---

