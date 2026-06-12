---
title: "EyeOS php error"
date: 2011-06-17
forum: Programming Talk
---

### Post by MasterNetra on 2011-06-17
I was wondering if anyone could help me, the EyeOS forums does have people asking for the solution of this problem but no answers. And I am hoping to get this solved sometime this century. No I am not a total noob to programming but I am unfamiliar with PHP. 

I am trying to upload EyeOS to my x10hosting account to tryout but after upload when I am going to it to setup it up, I get this php error: ```
 "Parse error: syntax error, unexpected T_PAAMAYIM_NEKUDOTAYIM in /home/**User Name Removed for post**/public_html/eyeos/eyeos/system/kernel/services/Meta/implementations/MetaDataConverter.php on line 62 
```

Code segment which goes from 61-63 has:
```
if (version_compare(PHP_VERSION, '5.3.0') >= 0) {

				return $handlerToLoad.::getInstance();

			} 
```
with ```
 return $handlerToLoad.'::getInstance();' 
``` at line 62.

If you need the whole file I have it attached as a zip.

---

### Post by MasterNetra on 2011-06-18
bump...

---

### Post by BkkBonanza on 2011-06-18
My guess is that,

return $handlerToLoad.::getInstance();

shouldn't have the extra "colons" there. The normal syntax for a member is $class.member.

BTW is that error message in Malay language? ( T_PAAMAYIM_NEKUDOTAYIM )

---

### Post by MasterNetra on 2011-06-19
> **BkkBonanza said:**
> My guess is that,

return $handlerToLoad.::getInstance();

shouldn't have the extra "colons" there. The normal syntax for a member is $class.member.

BTW is that error message in Malay language? ( T_PAAMAYIM_NEKUDOTAYIM )

I have no clue. All I know is the company behind eyeos is in Spain.

---

### Post by MasterNetra on 2011-06-19
*hits head* duh I have a trial of dreamweaver on my system and it handles php, i could open it in dreamweaver and see what it says.

**Update**
Turned line 63 into: ```
 return ($handlerToLoad.'::getInstance();'); 
``` and dreamweaver's syntax checker was happy. Gonna upload the file to see if she will run now.

---

### Post by MasterNetra on 2011-06-19
Yeap that did it! ... Though I got my hosting account suspended for high resource usage... -.- *sighs* I just can't win...

...well got my hosting site recovered and tryed again. Got it to load...but can't create a new account so i can use it... yet another obstacle... 

oh well the problem I posted for is solved so I guess I'll mark as such.

---

