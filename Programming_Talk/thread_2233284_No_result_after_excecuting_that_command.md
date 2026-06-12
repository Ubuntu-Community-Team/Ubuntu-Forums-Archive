---
title: "No result after excecuting that command"
date: 2014-07-07
forum: Programming Talk
---

### Post by mmmm3 on 2014-07-07
Hi, I found some code and it should work- but when I run it the bash gives me an empty row starting like ">   " that what shall I type in here to make that command working ?

[HTML]
for i in `seq 1 100`; do  
    curl http://mywebsite.com 
done[/HTML]

ANd than I found that:
[PHP]     <?php

  $count=0;
  $num=25;
  while($count <$num){



 $curl=curl_init();
 $site="http://...t";

 curl_setopt($curl,CURLOPT_URL,$site);
  curl_setopt($curl,CURLOPT_RETURNTRANSFER,1);


  $return=curl_exec($curl);
  curl_close($curl);

  echo $count  ."-";
  if($return)
  {echo "It worked <br>";}

  $count++;
        }
 ?>[/PHP]

But it does not succeed, with incresing the page view.(script works). What cann I improve here ?

---

### Post by deadflowr on 2014-07-07
Not a beginner subject.
Thread moved to Programming Talk

---

### Post by ofnuts on 2014-07-07
On sites where the page views are important, they have several techniques to keep people honest, the first one being to check the IP address...

---

### Post by mmmm3 on 2014-07-08
I also tried tor and reconnecting my router + deleting the history , and it did not work

---

### Post by ofnuts on 2014-07-08
You still get the same IP address... And even if that worked, you would have to obtain a new address for each page request, not for each script run.

---

### Post by mmmm3 on 2014-07-09
Hi,

> **ofnuts said:**
> You still get the same IP address...
Sorry, I don't understand your answer, because as soon as I use TOR(and change the identity after every page request manually for testing) i have a new IP and as soon as I reconnect my router to the internet I change my IP as well.

> **ofnuts said:**
> And even if  that worked, you would have to obtain a new address for each page  request, not for each script run.
How can I achieve that with C# or PHP ?
I found something like that [http://w-shadow.com/blog/2008/06/20/tor-how-to-new-identity-with-php/](http://w-shadow.com/blog/2008/06/20/tor-how-to-new-identity-with-php/) ,but if manually changing the ip(Tor "new identity" ) didn't work- so what exactly can I do ?
And what shall I look especially at when I use fiddler for analysing the traffic- session id's ?

Thanks for your support.

---

