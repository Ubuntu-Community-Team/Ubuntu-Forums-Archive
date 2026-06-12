---
title: "check internet availability with c++"
date: 2011-07-14
forum: Programming Talk
---

### Post by yahyai-0 on 2011-07-14
[SIZE=2]Hi

I want to know how to check the existence  of Internet  ?

from my knowledge and googling ..  that what I found
[/SIZE]

[LIST]
[*]**[SIZE=2]First method is to use ping.[/SIZE]**
[/LIST]
[SIZE=2]```
if (system("ping -c1 -s1 www.google.com"))
    {
        cout<<"There is no internet connection  \n";
}

```-But it is some how slow , someone in the IRC said to me to use fork() and exec() [COLOR=DarkRed]but I dont how to use it will ![/COLOR]
[/SIZE][SIZE=2]
[/SIZE]
[LIST]
[*][B][SIZE=2][COLOR=DarkGreen]The Best way : using pipe : thats what I used in my programs[/COLOR]
[/SIZE][/B]
[/LIST]
[SIZE=2]```
FILE *output;

    if(!(output = popen("/sbin/route -n | grep -c '^0\\.0\\.0\\.0'","r"))){
        return 1;
    }
    unsigned int i;
    fscanf(output,"%u",&i);
    if(i==0)
           cerr<<"There is no internet connection\n";
    else if(i==1)
        cerr<<"There is internet connection\n";
    }
    pclose(output);
```[/SIZE][SIZE=2][COLOR=Black]I found this way better than the other. cuz it is super fast>>

[/COLOR][/SIZE][SIZE=2]
[/SIZE]
[LIST]
[*][SIZE=2]**the socket way :** To use socket.h but I dont know how to use it , I[COLOR=DarkRed]f the socket dev can provide us with easy class thats will be better[/COLOR] :)[/SIZE]
[*][B][SIZE=2]Networkmanager method using dbus (thanks [/SIZE][ssam]("http://ubuntuforums.org/member.php?u=3369")) [COLOR=DarkRed]I dont know how to use dbus..[/COLOR]
[/B]
[*]**libcurl thanks (**[dwhitney67]("http://ubuntuforums.org/member.php?u=322753")):
[/LIST]
[SIZE=2]```
CURL *curl;
  CURLcode res;
 
  curl = curl_easy_init();
  if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "www.google.com");
  while ((res = curl_easy_perform(curl)) != CURLE_OK)
  {
    switch (res)
    {
        case CURLE_COULDNT_CONNECT:
        case CURLE_COULDNT_RESOLVE_HOST:
        case CURLE_COULDNT_RESOLVE_PROXY:
             cout<<"Internet dose not exist";
            break;
        default:
            cerr<<"Request failed:"<<curl_easy_strerror(res)<<endl;
            exit(1);
    }
    } 
 
    /* always cleanup */ 
    curl_easy_cleanup(curl);
      cout<<"Internet exist";
```[/SIZE][B]I made the thread like this to be good reference for the people who search about it
now cold u help them :)[/B] ,, [COLOR=DarkRed]**answer the red lines!! **[/COLOR]?

---

### Post by dwhitney67 on 2011-07-14
Why would your program care if Google is available?  Checking that particular site is a bit arbitrary, isn't it?

I'm not sure why your program requires Internet access, but for whatever operation that it performs (say you want to download HTML content), then just do it.  If it fails, then I suppose you can assume that either 1) the site is not available, or 2) the Internet is not available.

Do some research on the following terms; these are typical if you fail to get to a particular site.

1.  Connection refused.
2.  Connection timed out
3.  No route to host

Anyhow, using system() commands is a bad approach to solving any problem.  Status is not returned by that function, other than to indicate whether the command was executed or not.  That status is not what you are looking for (for example, you probably would care more about the status of ping, not system()).

Consider using the Curl Library for your needs.

---

### Post by yahyai-0 on 2011-07-14
> Why would your program care if Google is available?  Checking that particular site is a bit arbitrary, isn't it?yep , but I ping to google cuz it is there every time ...

> I'm not sure why your program requires Internet access, but for whatever  operation that it performs (say you want to download HTML content),  then just do it.  If it fails, then I suppose you can assume that either  1) the site is not available, or 2) the Internet is not available.
I wanna check Internet existence cuz somtimes it better to know why thing have not happend ....alot of cases

> Anyhow, using system() commands is a bad approach to solving any  problem.  Status is not returned by that function, other than to  indicate whether the command was executed or not.  That status is not  what you are looking for (for example, you probably would care more  about the status of ping, not system()).if ping fail to connect system fail (try it)
> 

Consider using the Curl Library for your needs.     thanks alot.I did it but I prefer  /sbin/route -n | grep -c '^0\.0\.0\.0' cuz it super fast but how I can know whether it return 0 or 1
```

bool Update::isConnected ()
{

  CURL *curl;
  CURLcode res;
 
  curl = curl_easy_init();
  if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "www.google.com");
  while ((res = curl_easy_perform(curl)) != CURLE_OK)
  {
    switch (res)
    {
        case CURLE_COULDNT_CONNECT:
        case CURLE_COULDNT_RESOLVE_HOST:
        case CURLE_COULDNT_RESOLVE_PROXY:
            return false;
            break;
        default:
            cerr<<"Request failed:"<<curl_easy_strerror(res)<<endl;
            exit(1);
    }
    } 
 
    /* always cleanup */ 
    curl_easy_cleanup(curl);
      return true;
  }
```

---

### Post by dwhitney67 on 2011-07-14
> **yahyai-0 said:**
> 
if ping fail to connect system fail (try it)

You're right; maybe I was thinking how system() was implement long ago in Unix systems.

---

### Post by cgroza on 2011-07-14
If you use curl, I think there is an error code that will describe your case.
There is no need to check it yourself.

---

### Post by ssam on 2011-07-14
you can also ask networkmanager if there is a connection. might be overkill here though.

---

### Post by yahyai-0 on 2011-07-14
> **cgroza said:**
> If you use curl, I think there is an error code that will describe your case.
There is no need to check it yourself.

thanks cgroza , I hv searched about them...

---

### Post by yahyai-0 on 2011-07-14
> **ssam said:**
> you can also ask networkmanager if there is a connection. might be overkill here though.

_thanks alot _[ssam]("http://ubuntuforums.org/member.php?u=3369") good idea , the problem I dont know how to use dbus

---

