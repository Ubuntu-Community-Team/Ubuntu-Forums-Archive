---
title: "Get information of google maps"
date: 2010-11-26
forum: Programming Talk
---

### Post by toanhoi on 2010-11-26
Hi,everybody.I am doing a project which gets information of google maps when i send a coordinate[COLOR=#000000]s .This is my code but it has a error .Can you help me
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main ( void ) {
int socket_handle ;
struct sockaddr_in socket_detials ;
char * input_buffer;
char * pinput_buffer ;
ssize_t bytes_received ;
ssize_t bytes_sent ;
char * phttpget ;
char * httpget =
"GET / HTTP/1.0\r\n"
"Host: http://maps.google.com/maps?f=d&source=s_d&saddr=N%E1%BB%99i+b%E1%BB%99+B%C3%A1ch+Khoa,+Hai+Ba+Trung+district,+Hanoi,+Vietnam&daddr=Tr%E1%BA%A7n+%C4%90%E1%BA%A1i+Ngh%C4%A9a&hl=en&geocode=FS6KQAEdNA9PBinZZiSzd6w1MTEVxEjhiJ-TIg%3BFdl9QAEdoxBPBg&mra=mift&mrsp=1&sz=16&sll=21.006894,105.844532&sspn=0.008674,0.013154&g=21.007,105.843&ie=UTF8&z=16\r\n"
"\r\n";

phttpget = httpget ;
bytes_sent = 0 ;

input_buffer = malloc(1024);
if ( input_buffer == NULL ) {
printf ( "Sorry, couldnt allocate memory for input buffer\n" );
return -1 ;
}
memset ( input_buffer, 0, 1024 ) ;

memset ( &socket_detials , 0 , sizeof(struct sockaddr_in) );

socket_handle = socket ( AF_INET, SOCK_STREAM, 0) ;
if ( socket_handle == -1 ) {
printf ( "Could not create socket\n" ) ;
return -1 ;
}
socket_detials.sin_family = AF_INET ;
socket_detials.sin_addr.s_addr=inet_addr("74.125.71.105");
socket_detials.sin_port = htons(80);

if ( connect (socket_handle,(struct sockaddr*)&socket_detials, sizeof ( struct sockaddr)) == -1 ){
printf ( "Couldnt connect to server\n" ) ;
return -1 ;
}

printf ( "Attempting to send %d bytes to server\n" , strlen ( httpget ) );
for(; ; ) {
bytes_sent = send ( socket_handle , phttpget, strlen(phttpget), 0 ) ;
if ( bytes_sent == -1 ) {
printf ( "An error occured sending data\n" );
return -1 ;
}
if ( httpget+strlen(httpget) == phttpget )
break ;
phttpget += bytes_sent ;
}

for (;  ; ){
bytes_received = recv ( socket_handle , input_buffer , 1023, 0 ) ;
if ( bytes_received == -1 ) {
printf ( "An error occured during the receive procedure \n" ) ;
return 0 ;
}
if ( bytes_received == 0 )
break ;
pinput_buffer = input_buffer + bytes_received ;
*pinput_buffer = 0 ;
printf ( "%s" , input_buffer ) ;
}

printf ( "\nFinished receiving data\n" ) ;
return 0 ;
}
[/COLOR]

---

### Post by smartbei on 2010-11-27
I'm not sure what information you are trying to get, or why you are doing this in C (something like python would be a lot more friendly), but I would recommend re-thinking your approach to the problem :-).

Anyway, your HTTP header is close but not quite right. You need to encode the URL itself so it doesn't have spaces (replace them with %20). And it should be:
```

char * httpget = "GET URL HTTP/1.1\r\n\r\n"

// So in your case:
char * httpget = "GET http://maps.google.com/maps?f=d&source=s_d&saddr=N%E1%BB%99i+b%E1%BB%99+B%20%C3%A1ch+Khoa,+Hai+Ba+Trung+district,+Hanoi,+Vietn%20am&daddr=Tr%E1%BA%A7n+%C4%90%E1%BA%A1i+Ngh%C4%A9a&%20hl=en&geocode=FS6KQAEdNA9PBinZZiSzd6w1MTEVxEjhiJ-TIg%3BFdl9QAEdoxBPBg&mra=mift&mrsp=1&sz=16&sll=21.%20006894,105.844532&sspn=0.008674,0.013154&g=21.007,%20105.843&ie=UTF8&z=16 HTTP/1.1\r\n\r\n";

```

---

