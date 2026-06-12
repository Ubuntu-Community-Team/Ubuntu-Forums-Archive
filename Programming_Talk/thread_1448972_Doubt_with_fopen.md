---
title: "Doubt with fopen"
date: 2010-04-07
forum: Programming Talk
---

### Post by indarkness on 2010-04-07
Hi everybody!!!
 
Well I'm programing the typical server-client to send from the client to the server, a file.
The problem I'm having it's I can not write in the file I open in the server's side,and I don't know why. When I compiled, sometimes I've got a segment violation and other I don't have got the error, but in both cases I can't open the output file... I know the problem is using the function Fwrite(), but I can't understand why it doesn't work.
I've forgotten to say, that I send the name of the file from the client to the server.
Could you give me a helping hand?
 
Here is the code I use for the server:
 
```

#ifndef unix
#define WIN32
#include <windows.h>
#include <winsock.h> 
#else
#define closesocket close
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#endif
 
#include <stdio.h>
#include <string.h>
 
#define PROTOPORT       8000            /* puerto por defecto que usamos */
#define QLEN            6               /* tamaÃ±o de la cola que somos capaces de soportar  */
 
int     visits      =   0;              /* counts client connections    */
/*------------------------------------------------------------------------
 * Program:   server
 *
 * 
 *------------------------------------------------------------------------
 */
main(argc, argv)
int     argc;
char    *argv[];
{
        struct  hostent  *ptrh;  /* puntero a los parametros del host   */
        struct  protoent *ptrp;  /* puntero a los parametros del protocolo*/
        struct  sockaddr_in sad; /* estructura que guarda la direccion del server */
        struct  sockaddr_in cad; /* estructura que guarda la direccion del cliente*/
        int     sd, sd2;         /* nombres de los sockets usados                 */
        int     port;            /* puerto que usamos                */
        int     alen;            /* tamaÃ±o de la direccion IP                   */
        char    buf[1000];       /* buffer donde se alamacena los mensajes que envia el server */
 
#ifdef WIN32
        WSADATA wsaData;
        WSAStartup(0x0101, &wsaData);
#endif
        memset((char *)&sad,0,sizeof(sad)); /* limpiamos la estructura sockaddr */
        sad.sin_family = AF_INET;         /* definimos la familia de internet  */
        sad.sin_addr.s_addr = INADDR_ANY; /* obtenemos nuestra direcion IP   */
 
        /* Check command-line argument for protocol port and extract    */
        /* port number if one is specified.  Otherwise, use the default */
        /* port value given by constant PROTOPORT                       */
 
        if (argc > 1) {                 /* if argument specified        */
                port = atoi(argv[1]);   /* convert argument to binary   */
        } else {
                port = PROTOPORT;       /* use default port number      */
        }
        if (port > 0)                   /* test for illegal value       */
                sad.sin_port = htons((u_short)port);
        else {                          /* print error message and exit */
                fprintf(stderr,"bad port number %s\n",argv[1]);
                exit(1);
        }
 
        /* Map TCP transport protocol name to protocol number */
 
        if ( ((int)(ptrp = getprotobyname("tcp"))) == 0) {
                fprintf(stderr, "cannot map \"tcp\" to protocol number");
                exit(1);
        }
 
        /* Create a socket */
 
        sd = socket(PF_INET, SOCK_STREAM, ptrp->p_proto);
        if (sd < 0) {
                fprintf(stderr, "socket creation failed\n");
                exit(1);
        }
 
        /* Bind a local address to the socket */
 
        if (bind(sd, (struct sockaddr *)&sad, sizeof(sad)) < 0) {
                fprintf(stderr,"bind failed\n");
                exit(1);
        }
 
        /* Specify size of request queue */
 
        if (listen(sd, QLEN) < 0) {
                fprintf(stderr,"listen failed\n");
                exit(1);
        }
 
        /* Main server loop - accept and handle requests */
 
 
     alen = sizeof(cad);
         if ( (sd2=accept(sd, (struct sockaddr *)&cad, &alen)) < 0) {
                        fprintf(stderr, "accept failed\n");
                        exit(1);
     }
 
 
 
 
     /*Creo el fichero que quiero guardar*/
     FILE *aux1;
     char nombre[1000];
 
 
     /*Leo el nombre del fichero que me envia el cliente y creo dicho archivo en el server*/
      memset(nombre,0,sizeof(nombre));
    read(sd2,nombre,sizeof(nombre));
    strcat(nombre,"s");    
 
    aux1=fopen(nombre,"w+");
    fflush(NULL);
    memset(buf,0,sizeof(buf));
 
     /*bucle que recive el contenido del fichero*/
        while (read(sd2,buf,sizeof(buf))>1) {
 
        //read(sd2,buf,sizeof(buf));
        printf("%s \n",buf);
        fwrite(buf,8,sizeof(buf),aux1);
        memset(buf,0,sizeof(buf));
 
        }
 
        fclose(aux1);
 
        closesocket(sd2);
}
 

```ANd here the client code:
 
```

/* client.c - code for example client program that uses TCP */
 
#ifndef unix
#define WIN32
#include <windows.h>
#include <winsock.h>
#else
#define closesocket close
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#endif
 
#include <stdio.h>
#include <string.h>
 
#define PROTOPORT       8000           /* default protocol port number */
 
extern  int             errno;
char    localhost[] =   "localhost";    /* default host name            */
/*------------------------------------------------------------------------
 * Program:   client
 *
 
 *------------------------------------------------------------------------
 */
 
main(argc, argv)
int     argc;
char    *argv[];
{
        struct  hostent  *ptrh;  /* pointer to a host table entry       */
        struct  protoent *ptrp;  /* pointer to a protocol table entry   */
        struct  sockaddr_in sad; /* structure to hold an IP address     */
        int     sd;              /* socket descriptor                   */
        int     port;            /* protocol port number                */
        char    *host;           /* pointer to host name                */
        int     n;               /* number of characters read           */
        char    buf[1000];       /* buffer for data from the server     */
#ifdef WIN32
        WSADATA wsaData;
        WSAStartup(0x0101, &wsaData);
#endif
        memset((char *)&sad,0,sizeof(sad)); /* clear sockaddr structure */
        sad.sin_family = AF_INET;         /* set family to Internet     */
 
        /* Check command-line argument for protocol port and extract    */
        /* port number if one is specified.  Otherwise, use the default */
        /* port value given by constant PROTOPORT                       */
 
        if (argc > 2) {                 /* if protocol port specified   */
                port = atoi(argv[2]);   /* convert to binary            */
        } else {
                port = PROTOPORT;       /* use default port number      */
        }
        if (port > 0)                   /* test for legal value         */
                sad.sin_port = htons((u_short)port);
        else {                          /* print error message and exit */
                fprintf(stderr,"bad port number %s\n",argv[2]);
                exit(1);
        }
 
        /* Check host argument and assign host name. */
 
        if (argc > 1) {
                host = argv[1];         /* if host argument specified   */
        } else {
                host = localhost;
        }
 
        /* Convert host name to equivalent IP address and copy to sad. */
 
        ptrh = gethostbyname(host);
        if ( ((char *)ptrh) == NULL ) {
                fprintf(stderr,"invalid host: %s\n", host);
                exit(1);
        }
        memcpy(&sad.sin_addr, ptrh->h_addr, ptrh->h_length);
 
        /* Map TCP transport protocol name to protocol number. */
 
        if ( ((int)(ptrp = getprotobyname("tcp"))) == 0) {
                fprintf(stderr, "cannot map \"tcp\" to protocol number");
                exit(1);
        }
 
        /* Create a socket. */
 
        sd = socket(PF_INET, SOCK_STREAM, ptrp->p_proto);
        if (sd < 0) {
                fprintf(stderr, "socket creation failed\n");
                exit(1);
        }
 
        /* Connect the socket to the specified server. */
 
        if (connect(sd, (struct sockaddr *)&sad, sizeof(sad)) < 0) {
                fprintf(stderr,"connect failed\n");
                exit(1);
        }
 
 
 
        /*Creo y abro el fichero que voy a enviar*/
    FILE *aux1;
    if(argv[3]!=NULL){
        aux1=fopen(argv[3],"r");
    }
    else{
        perror("falta el nombre del fichero");
        exit(1);
    }
 
    /*Envio el nombre del fichero*/
        send(sd,argv[3],strlen(argv[3]),0);
    fflush(NULL);
 
        while (!feof(aux1) ) {
 
        memset(buf,0,sizeof(buf));
        fread(buf,8,sizeof(buf),aux1);
        printf("%s \n",buf);
        send(sd,buf,strlen(buf),0);
 
        }
 
    fclose(aux1);
        /* Close the socket. */
 
        closesocket(sd);
 
        /* Terminate the client program gracefully. */
 
        exit(0);
}
```

---

### Post by the_unforgiven on 2010-04-07
You can check for return value of fwrite() - if it fails, the return value is -1.
If that's the case, the global variable errno will give you the actual error - you can convert it into string using [strerror()]("http://linux.die.net/man/3/strerror")

Secondly, the fact that the crash isn't consistent means that it's more likely a race condition. I haven't even read through your code, so cannot give you exact pointers right now :(. Will try to do it later.

---

### Post by gmargo on 2010-04-07
> **the_unforgiven said:**
> You can check for return value of fwrite() - if it fails, the return value is -1.
If that's the case, the global variable errno will give you the actual error - you can convert it into string using [strerror()]("http://linux.die.net/man/3/strerror")


That is not true. **fwrite(3)** returns a short count or zero upon error, not -1. There is no way to get the actual error from a failed **fwrite(3)** library function.  

If you use the lower level system calls [**open(2)**, **write(2), close(2)**], then you can use **errno**.  (But don't try to mix buffered and unbuffered IO without a really good reason.)

---

### Post by gmargo on 2010-04-07
> **indarkness said:**
> I know the problem is using the function Fwrite(), but I can't understand why it doesn't work.

The problem is not **fwrite(3)**, it is **fopen(3)** - you are not checking the return code.  (In fact, you are not checking return codes for many calls that you should, like read(2), fread(3), send(2)).

---

### Post by Compyx on 2010-04-07
<pedantry-alert>

There are a lot more problems with the code, if I use `gcc -Wall -Wextra -ansi -Dunix' to compile either program, gcc refuses and spits out a boatload of warnings and errors.

[LIST]
[*]No #include <stdlib.h> so no prototype for exit().

[*]Casting a pointer to int just to check against 0, 0 is perfectly acceptable as a NULL-pointer constant, but I'd just drop the cast and check against NULL.

[*]Use of pre-standard C (declaration of main, using char* as a generic pointer type) and C99 features (declarations mixed with code).

[*]Non-portable return code (1) in exit() calls, EXIT_FAILURE would be more appropriate.

[*]Using int to store a size_t, using int to store a socklen_t, and so on and so on.
[/LIST]

To me, this looks like something cut and paste together from different sources (websites, books) without an understanding of what the code actually does.

</pedantry-alert>

---

### Post by indarkness on 2010-04-07
Thanks for replying!
 
> **gmargo said:**
> The problem is not **fwrite(3)**, it is **fopen(3)** - you are not checking the return code. (In fact, you are not checking return codes for many calls that you should, like read(2), fread(3), send(2)).
 
Ok I'll change that and check the return codes. But he problem like I said it was the fwrite,I think I've solved it, the error is here
 
```

 
fwrite(buf,8,**sizeof(buf)**,aux1);

```
 
I need using strlen(buf),because thus I write only the useful length of the buffer, and not all of it.
 
Thanks everbody!

---

### Post by soltanis on 2010-04-07
Also, don't mix UNIX calls with C standard library calls (i.e. fread with read on the same file). Stdio uses its own buffering system which tends to produce weird results when you mix them with the separately buffered system calls.

To check the return value of fopen, you should check to see if the pointer it returns is non-NULL:

```

/* my favorite convention for checking fopen */
FILE *fp;

if (!(fp = fopen(file, mode))) {
perror("fopen");
exit(1);
}

```

fread and fwrite are strange in that they don't set errno. You're supposed to check ferror, actually, because both functions can fail on both end of file and error conditions.

```

if (fwrite(buf, nitems, bufsize, fp) < nitems) {
if (ferror(fp)) {
fprintf(stderr, "there was an error but these functions are too stupid to set errno, so I dont know what it is");
exit(1);
}
}

```

Of course once the file is open, then I usually don't have problems reading or writing it; the usual errors come about during opening.

---

