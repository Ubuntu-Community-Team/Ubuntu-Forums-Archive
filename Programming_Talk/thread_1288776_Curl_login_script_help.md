---
title: "Curl login script help"
date: 2009-10-11
forum: Programming Talk
---

### Post by Girya on 2009-10-11
I'm trying to write a bash script to login and download some files but I'm stuck at the login page.

instead of the normal login form that asks for a username and password on the same page this form asks for a username on the first page then after supplying a username you are redirected to the same file that asks for your password.

I can use Curl to get to the second part of the form but I don't understand what to do next.

any suggestions would be welcome

thanks kevin

---

### Post by januzi on 2009-10-11
Take look at the curl options, there will be something like "[COLOR=Black]CURLOPT_HEADER[/COLOR]" and "CURLOPT_RETURNTRANSFER". Take a look at the result. There will cookie or session id. You have to set them at the next curl_exec. Just like in a browser.

---

### Post by Girya on 2009-10-11
> **januzi said:**
> Take look at the curl options, there will be something like "[COLOR=Black]CURLOPT_HEADER[/COLOR]" and "CURLOPT_RETURNTRANSFER". Take a look at the result. There will cookie or session id. You have to set them at the next curl_exec. Just like in a browser.

Thanks, I'll take a look. I think I'm not getting the flow of the script.

---

### Post by Girya on 2009-10-12
okay I figured this out. sortof. 

Here is the script: 
>   
  1 #!/bin/bash
  2 
  3 # curl script to retrieve some info 
  4 #download login page using lynx --source       #https://somelogin>some_file.txt
  5 #edit some_file.txt and replace post with get. --data string is #then found 
  6 #by loading page in browser and yanking $GET from browser address bar after     ? 

  8 #variables
  9 cookie_jar=cookies.tmp
 10 web_page=some_file.tmp
 11 username=<username>
 12 password=<password>
 13 
 14 curl --silent --cookie $cookie_jar \
 15         --output $web_page-1 \
 16         "https://some_login_page"
 17 
 18 curl --silent --cookie $cookie_jar --cookie-jar $cookie_jar \
 19         --location \
 20         --data "POST INFO HERE"\
 21         --output $web_page-2 \
 22         "https://some_login_page"
 23 
 24 curl --silent --cookie $cookie_jar --cookie-jar $cookie_jar \
 25         --location \
 26         --data "Action=Password&Password=$password" \
 27         --output $web_page-3 \
 28         "https://some_login_page"
 29 


hope the script helps someone

---

