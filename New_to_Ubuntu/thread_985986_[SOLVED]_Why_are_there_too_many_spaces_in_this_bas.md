---
title: "[SOLVED] Why are there too many spaces in this bash script?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-18
Hi, all:

I was wondering: why does this bash script have so many spaces in it?

[http://linuxshellaccount.blogspot.com/2008/09/bash-script-to-get-weather-forecasts.html](http://linuxshellaccount.blogspot.com/2008/09/bash-script-to-get-weather-forecasts.html)

When I use this script, the output I get has six or seven line breaks between each line of output, instead of being nicely formatted like in the example.

Anyone know why?

---

### Post by cmnorton on 2008-11-18
I am confused. Are you referring to the script or its output?

---

### Post by tarahmarie on 2008-11-18
The output.  It looks something like this:

> 
~/Documents/Scripts : Yes, Supreme Empress? $ weatherScript.sh 97223

Your Forecast:                   For Portland, OR 97223  

   
   
     
     
      
       
         Today 
           
         
          
           Hi: 55 &deg;F 
          
           Lo: 43 &deg;F 
          
         
         Mostly cloudy. Areas of fog in the morning...locally dense especially Interstate 5 westward. Highs a... more
  
          
       
      
       
         Wednesday 
           
         
          
           Hi: 55 &deg;F 
          
           Lo: 44 &deg;F 
          
         
         Mostly cloudy. Patchy fog in the morning. Highs in the mid 50s. Southeast wind 5 to 15 mph.... more
  
          
       
      
        
     
    


See how much extra space is in there?  Why would it do that?

---

### Post by redseventyseven on 2008-11-18
Probably because the source of the data (in this case weatherbug.com) put in some extra line breaks into their text.

I think that's what the script author was referring to when he says: "*Click on either picture to see it as the artist intended it to be seen before the producers ruined everything ;)*"

---

### Post by tarahmarie on 2008-11-18
Is there any way to fix this?

---

