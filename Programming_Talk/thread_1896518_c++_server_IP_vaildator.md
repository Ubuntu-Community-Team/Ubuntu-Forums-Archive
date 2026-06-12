---
title: "c++ server IP vaildator"
date: 2011-12-17
forum: Programming Talk
---

### Post by highspider on 2011-12-17
I wrote this for my dads server more like my hobby server.   

I just want some pointers from the Linux world.  Since you guys always know the tricks
I took out my comments out they are in the text file 

```

#define MAIL_PROGRAM "/usr/sbin/sendmail" 
#include <curl/curl.h>             
#include <fstream>                   
using std::fstream;         

const char * Self_ID = "bongrip@gmail.com";                            
const char * Subject = "Web IPchanged";                                 
const char * Your_Server ="ServerNAME";
const int MAX = 16;
const char* runningIP_file_loc ="/tmp/ip.txt";
const char* savedIP_file_loc = "/root/ip.txt";
const char* IPsite = "http://automation.whatismyip.com/n09230945.asp";   
int check = 0;
char running_ip[MAX] = "000.000.000.000";      
char savedIP[MAX] = "000.000.000.000";

void sendmail(const char * Self_ID, const char * Subject, const char * Your_Server,
char * running_ip, char * savedIP);
void get_page( const char* url, const char* file_name );

int main(){
get_page( IPsite, runningIP_file_loc );

fstream fin1;
fin1.open(runningIP_file_loc);
fin1.getline(running_ip, 16);
fin1.close();
fstream fin2;
fin2.open(savedIP_file_loc);
fin2.getline(savedIP, 16);
fin2.close();

for ( int i = 0; i < MAX; i++ ){
    if ( running_ip[i] != savedIP[i] )
        check++;  
}
if ( check != 0 )
    sendmail(Self_ID, Subject, Your_Server, running_ip, savedIP);
return 0;
}

void sendmail(const char * Self_ID, const char * Subject, const char * Your_Server, char * running_ip, char * savedIP){
 FILE *mail;                        
    mail = popen (MAIL_PROGRAM " -t", "w");
    fprintf (mail, "To: %s\n", Self_ID );
    fprintf (mail, "From: %s\n", Your_Server );
    fprintf (mail, "Subject: %s\n", Subject);
    fprintf (mail, "\n");
    fprintf (mail, "The servers IP has been changed from\n %s\n", savedIP);
    fprintf (mail, "\tTO\n %s\n", running_ip);
    fprintf (mail, "\nPlease correct your redirect [@ host] to %s with your Internet domain registrar\n\n", running_ip);
    fprintf (mail, "Remember to update the saved IP in file %s after correcting this issue", savedIP_file_loc);
        fprintf (mail, "\n.\n");
        pclose (mail);
}

void get_page( const char* url, const char* file_name ){
    CURL* easyhandle = curl_easy_init() ;
    curl_easy_setopt( easyhandle, CURLOPT_URL, url ) ;
    std::FILE* file = std::fopen( file_name, "w" ) ;
    curl_easy_setopt( easyhandle, CURLOPT_WRITEDATA, file ) ;
    curl_easy_perform( easyhandle );
    curl_easy_cleanup( easyhandle );
}

```

---

### Post by ofnuts on 2011-12-17
Two thoughts:

1) Using C for this seems overkill, a mere shell script could do it.

2) The real solution to the original problem is to use [Dynamic DNS]("http://en.wikipedia.org/wiki/Dynamic_DNS")

---

### Post by highspider on 2011-12-17
> **ofnuts said:**
> Two thoughts:
1) Using C for this seems overkill, a mere shell script could do it. 
    I just thought It would be cooler in c++ because I like c++.  
     here it is "basicly" in shell script 

```

#!/bin/bash

if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
else
   OLD_IP=( $( /bin/cat /root/ip.txt ) )
   NEW_IP=( $( wget -q -O - http://automation.whatismyip.com/n09230945.asp) )
   if [ "$NEW_IP" = "$OLD_IP" ]; then
      echo "IP's the same"
    else
      echo "Should call mail"
      echo "IP's are different"
   fi
fi

```> **ofnuts said:**
> 
2) The real solution to the original problem is to use [Dynamic DNS]("http://en.wikipedia.org/wiki/Dynamic_DNS")
I'm looking into this 

THANK YOU!

---

