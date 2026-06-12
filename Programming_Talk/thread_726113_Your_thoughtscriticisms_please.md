---
title: "Your thoughts/criticisms please"
date: 2008-03-16
forum: Programming Talk
---

### Post by dunryc on 2008-03-16
Hi all quite pleased with myself today as i've written a quick bash script that ill probably use myself on a daily basis. It downloads a few pdf's from "The Guardians" site then concatenates them into one pdf for use on the journey to work on my pda, I  wouldn't mind any criticisms or help improving it if any ones got the time to run it and have a look for me :-) 

:-

> 
#!/bin/bash
#by dunryc 16/03/2008
#download and combine the gaurdians daily g24 pdf's so we get one guardian pdf 
#dont run this in a folder wich contains pdf file you want to keep as it will detlete them 
#i deleted all pdfs to keep the script as short and simple as possible 
TODAY=`date +%Y_%m_%d`
wget -r -l1 -H -t1 -nd -N -np -R.html -A.pdf -erobots=off  [http://www.guardian.co.uk/g24](http://www.guardian.co.uk/g24) 
pdftk *.pdf cat output guardian 
rm *.pdf 
rename  guardian "Gaurdian_$TODAY".pdf



---

### Post by Jessehk on 2008-03-16
Rather than deleting all the pdf's in the CWD (I'm assuming you do it to get rid of the old ones), try to think of a way to delete just the downloaded ones. That way, you don't risk deleting important files just because you ran the script in the wrong location.

---

### Post by dunryc on 2008-03-16
> Rather than deleting all the pdf's in the CWD (I'm assuming you do it to get rid of the old ones), try to think of a way to delete just the downloaded ones. That way, you don't risk deleting important files just because you ran the script in the wrong location.

thanks for the heads up this should do the trick

> 
#!/bin/bash
#by dunryc 16/03/2008
#download and combine the gaurdians daily g24 pdf's so we get #one guardian pdf simple as possible 
TODAY=`date +%Y_%m_%d`
mkdir temppdf
cd temppdf 
wget -r -l1 -H -t1 -nd -N -np -R.html -A.pdf -erobots=off  [http://www.guardian.co.uk/g24](http://www.guardian.co.uk/g24) 
cd ..
pdftk temppdf/*.pdf cat output "Gaurdian_$TODAY".pdf
rm -r -f temppdf 

 it also give the added bunus of not having to remname the output pdf !! 

thanks

---

