---
title: "C Socket server problem"
date: 2009-07-26
forum: Programming Talk
---

### Post by stuffradio on 2009-07-26
Hi,

I have a socket server that runs fine with the example when it's untouched.

I modified it and I'm compiling it with gcc linking it to the C Mysql api. The way I have it, for some reason makes it shut down.

I am thinking it might have to do with some function that mysql returns that makes it do that. If someone with knowledge in this area could guide me, that would be great!

Code with the part that I modified:

```

/* ------------------------------------------------
 *                                 echoTcp
 * ------------------------------------------------
 */
int echoTcp (int sock)
{
    int             nbytes;
    char            buffer[MAXMSG];
/* ------------------------------------------------
 *                               connect to MySQL host
 * ------------------------------------------------
 */

  int i = 0, k;
   MYSQL *conn;
   MYSQL_RES *res;
   MYSQL_ROW row;

   char *server = "127.0.0.1";
   char *user = "";
   char *password = ""; /* set me first */
   char *database = "";
   char str[100] = "07/24/09,310640101057789,ON,OFF,ON,ON,OFF,513,2,7,0,0", columns[MAX_COLUMNS][MAX_STR_LEN], *p;
   char * pch;
   char strvals[] = "";
   char *col1 = "";
   char *col2 = "";
   char *col3 = "";
   char *col4 = "";
   char *col5 = "";
   char *col6 = "";
   char *col7 = "";
   char *col8 = "";
   char *col9 = "";
   char *col10 = "";
   char *col11 = "";
   char *col12 = "";
   char *quer;
   quer = malloc(1024);
   const int strsize = sizeof(str);
   conn = mysql_init(NULL);

   /* Connect to database */
   if (!mysql_real_connect(conn, server,
         user, password, database, 0, NULL, 0)) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

    nbytes = read (sock, buffer, MAXMSG);
    if (nbytes > 0)
    {

/* -----------------------------------------------
 *                  This is the section for MySQL
 *                  data.
 */
p = strtok (buffer, ",");
while (p)
{
strncpy(columns[i++],p,MAX_STR_LEN);
p = strtok(NULL, ",");
}

col1 = columns[0];
col2 = columns[1];
col3 = columns[2];
col4 = columns[3];
col5 = columns[4];
col6 = columns[5];
col7 = columns[6];
col8 = columns[7];
col9 = columns[8];
col10 = columns[9];
col11 = columns[10];
col12 = columns[11];

sprintf(quer, "INSERT INTO `systemreports`(ReportDate, IDNumber, PowerStatus, Telemetry, WaterPumpA, WaterPumpB, AirPumpA, AirPumpB, DailyWaterUse, WaterQuality, UVStatus, OtherStatus) VALUES('%s','%s','%s','%s','%s','%s','%s','%s','%s','%s','%s','%s')",
col1,col2,col3,col4,col5,col6,col7,col8,col9,col10,col11,col12);
if (mysql_query(conn,quer))
{
      fprintf(stderr, "%s\n", mysql_error(conn));
      
}


/* close connection */
   mysql_free_result(res);
   mysql_close(conn);

        /* Echo data read and log the time. */
        write (sock, buffer, nbytes);
        gSockTime[sock] = time(NULL);
        return nbytes;
    }
    else
    {
        /* End-of-file or error. */
        closeSock (sock);        
    }
}

```

Full code:
```

/*
 * Based on:
 * http://www.gnu.org/software/libc/manual/html_mono/libc.html#Server%20Example
 */

#include "/mnt/ext/opt/mysql/include/mysql/mysql.h"
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/select.h>
#include <sys/param.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <string.h>
#include <syslog.h>
#include <stdarg.h>
#include <time.h>


#define PORT             1730   /* default port to listen on */
#define MAXMSG          10240
#define MAX_QUEUED_CONNS    5
#define MAX_SOCK_IDLE      10   /* minutes */
#define SECS_PER_MIN       60
#define MAX_STR_LEN 100
#define MAX_COLUMNS 100


/*
 * Global vars.
 */
static const char  gVersion[] = "@(#) tcpechoserver v1.4 " __DATE__;

const char         gScaryMsg[] =
    "\r\n\r\n                             WARNING\r\n"
    "      Unauthorized access to this system is forbidden and will be\r\n"
    "      prosecuted by law. By accessing this system, you agree that your\r\n"
    "      actions may be monitored if unauthorized usage is suspected.\r\n\r\n"
    "      Your IP address has been logged: ";

const char         gDiscMsg[] = "\r\nDisconnecting due to inactivity\r\n";

char               gHostNameBuf[512];
struct sockaddr_in gServerName;
int                gMaxFd;
int                gNumberClients;
int                gDebug;
int                gTcpListenSock;
int                gUdpSock;
time_t             gMaxSockIdle = MAX_SOCK_IDLE * SECS_PER_MIN;
time_t             gSockTime[FD_SETSIZE];
fd_set             gActive_fd_set;

#ifdef __CYGWIN__
/* Set default log file name for Cygwin build. */
char               gLogFilename[FILENAME_MAX] = { "C:/TEMP/tcpecho.log" };
#define SYSLOG   mySyslog
/* ------------------------------------------------
 *                                       mySyslog
 * ------------------------------------------------
 */
static void mySyslog (int level, const char *fmt, ...)
{
    static FILE    *logFile = NULL;
    va_list         ap;
    char            buf[1024];
    time_t          logTime;

    if (logFile == NULL)
    {
        logFile = fopen (gLogFilename, "a");
    }

    if (logFile != NULL)
    {
        va_start (ap, fmt);
        vsnprintf (buf, sizeof buf, fmt, ap);
        va_end (ap);

        logTime = time (NULL);
        fprintf (logFile, "%24.24s: %s\n", ctime (&logTime), buf);
        fflush (logFile);
    }
}
#else
#define SYSLOG   syslog
#endif


/* ------------------------------------------------
 *                               getRemoteHostname
 * ------------------------------------------------
 */
const char * getRemoteHostname (struct sockaddr_in sin)
{
    struct hostent *hp;

    hp = gethostbyaddr ((char *) &sin.sin_addr,
                        sizeof sin.sin_addr, AF_INET);
    if (hp)
    {
        /*
         * We found a corresponding hostname, format the string one way...
         */
        snprintf (gHostNameBuf, sizeof gHostNameBuf, "%s [%s]", hp->h_name,
                  inet_ntoa (sin.sin_addr));
    }
    else
    {
        /*
         * This host not in the host tables or Domain Name Server.
         */
        snprintf (gHostNameBuf, sizeof gHostNameBuf, "[%s]",
                  inet_ntoa (sin.sin_addr));
    }

    return gHostNameBuf;
}

/* ------------------------------------------------
 *                                    bindToPort 
 * ------------------------------------------------
 */
int bindToPort (int sockStyle)
{
    int             sock;
    int             opt;

    /* Create the socket. */
    sock = socket (PF_INET, sockStyle, 0);
    if (sock < 0)
    {
        SYSLOG (LOG_USER, "socket failed");
        exit (EXIT_FAILURE);
    }

    /*
     * Set the "REUSEADDR" option on this socket. This will allow us to
     * bind() to it EVEN if there already connections in progress on this
     * port number. Otherwise, we would get an "Address already in use"
     * error.
     */
    if (setsockopt (sock, SOL_SOCKET, SO_REUSEADDR, &opt, sizeof (opt)) < 0)
    {
      SYSLOG (LOG_USER, "setsockopt failed");
      exit (EXIT_FAILURE);
    }

    if (bind (sock, (struct sockaddr *) &gServerName, sizeof gServerName) < 0)
    {
        SYSLOG (LOG_USER, "bind failed");
        exit (EXIT_FAILURE);
    }

    return sock;
}

/* ------------------------------------------------
 *                                    closeSock
 * ------------------------------------------------
 */
void closeSock (int sock)
{
    SYSLOG (LOG_USER, "connection %d: disconnecting.", sock);
    close (sock);
    FD_CLR (sock, &gActive_fd_set);
    gNumberClients--;
}

/* ------------------------------------------------
 *                                 echoTcp
 * ------------------------------------------------
 */
int echoTcp (int sock)
{
    int             nbytes;
    char            buffer[MAXMSG];
/* ------------------------------------------------
 *                               connect to MySQL host
 * ------------------------------------------------
 */

  int i = 0, k;
   MYSQL *conn;
   MYSQL_RES *res;
   MYSQL_ROW row;

   char *server = "127.0.0.1";
   char *user = "";
   char *password = ""; /* set me first */
   char *database = "";
   char str[100] = "07/24/09,310640101057789,ON,OFF,ON,ON,OFF,513,2,7,0,0", columns[MAX_COLUMNS][MAX_STR_LEN], *p;
   char * pch;
   char strvals[] = "";
   char *col1 = "";
   char *col2 = "";
   char *col3 = "";
   char *col4 = "";
   char *col5 = "";
   char *col6 = "";
   char *col7 = "";
   char *col8 = "";
   char *col9 = "";
   char *col10 = "";
   char *col11 = "";
   char *col12 = "";
   char *quer;
   quer = malloc(1024);
   const int strsize = sizeof(str);
   conn = mysql_init(NULL);

   /* Connect to database */
   if (!mysql_real_connect(conn, server,
         user, password, database, 0, NULL, 0)) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

    nbytes = read (sock, buffer, MAXMSG);
    if (nbytes > 0)
    {

/* -----------------------------------------------
 *                  This is the section for MySQL
 *                  data.
 */
p = strtok (buffer, ",");
while (p)
{
strncpy(columns[i++],p,MAX_STR_LEN);
p = strtok(NULL, ",");
}

col1 = columns[0];
col2 = columns[1];
col3 = columns[2];
col4 = columns[3];
col5 = columns[4];
col6 = columns[5];
col7 = columns[6];
col8 = columns[7];
col9 = columns[8];
col10 = columns[9];
col11 = columns[10];
col12 = columns[11];

sprintf(quer, "INSERT INTO `systemreports`(ReportDate, IDNumber, PowerStatus, Telemetry, WaterPumpA, WaterPumpB, AirPumpA, AirPumpB, DailyWaterUse, WaterQuality, UVStatus, OtherStatus) VALUES('%s','%s','%s','%s','%s','%s','%s','%s','%s','%s','%s','%s')",
col1,col2,col3,col4,col5,col6,col7,col8,col9,col10,col11,col12);
if (mysql_query(conn,quer))
{
      fprintf(stderr, "%s\n", mysql_error(conn));
      
}


/* close connection */
   mysql_free_result(res);
   mysql_close(conn);

        /* Echo data read and log the time. */
        write (sock, buffer, nbytes);
        gSockTime[sock] = time(NULL);
        return nbytes;
    }
    else
    {
        /* End-of-file or error. */
        closeSock (sock);        
    }
}

/* ------------------------------------------------
 *                               echoUdp
 * ------------------------------------------------
 */
void echoUdp (int sock)
{
    int                nbytes;
    int                size;
    struct sockaddr_in sin;
    char               buffer[MAXMSG];

    sin.sin_family      = AF_INET;
    sin.sin_addr.s_addr = INADDR_ANY;
    sin.sin_port        = gServerName.sin_port;
    size                = sizeof sin;

    nbytes = recvfrom (sock, buffer, MAXMSG, 0,
                       (struct sockaddr *) &sin, &size);
    if (nbytes < 0)
    {
        SYSLOG (LOG_USER, "recfrom failed");
        return;
    }

    /* Log the message. */
    if (gDebug)
    {
        SYSLOG (LOG_USER, "Rcvd UDP (%d bytes) from: [%s]  Port: %d",
                nbytes, inet_ntoa (sin.sin_addr), ntohs(sin.sin_port));
    }

    /*
     * If the source port is 0, we can't send the message back.
     */
    if ( ntohs(sin.sin_port) != 0 )
    {
        /* Echo the message back to the sender. */
        nbytes = sendto (sock, buffer, nbytes, 0,
                         (struct sockaddr *) &sin, size);
        if (nbytes < 0)
        {
            SYSLOG (LOG_USER, "sendto failed");
            return;
        }
    }
}

/* ------------------------------------------------
 *                               checkIdleSockets
 * ------------------------------------------------
 */
void checkIdleSockets ( void )
{
    int         sock;
    time_t      currentTime = time(NULL);

    //if (gDebug) SYSLOG(LOG_USER, "checkIdleSockets");

    /*
     * Check for an active socket that has been idle
     * for longer than gMaxSockIdle seconds.
     */
    for (sock = 0; sock <= gMaxFd; ++sock)
    {
        if (FD_ISSET (sock, &gActive_fd_set)  &&
            ((currentTime - gSockTime[sock]) > gMaxSockIdle ) &&
            (sock != gTcpListenSock) &&
            (sock != gUdpSock))
        {
            write (sock, gDiscMsg, sizeof gDiscMsg);
            closeSock (sock);
        }
    }
}

/* ------------------------------------------------
 *                                  acceptNewSock
 * ------------------------------------------------
 */
void acceptNewSock ( void )
{
    struct sockaddr_in clientName;
    int                acceptSock;
    int                size;
    char               buffer[MAXMSG];

    /* Accept new connection request on original socket. */
    size = sizeof clientName;
    acceptSock = accept (gTcpListenSock,
                         (struct sockaddr *) &clientName,
                         &size);
    if (acceptSock < 0)
    {
        SYSLOG (LOG_USER, "accept failed");
        exit (EXIT_FAILURE);
    }

    SYSLOG (LOG_USER,
            "connection %d from %s, port %hu.",
            acceptSock,
            getRemoteHostname (clientName),
            ntohs (clientName.sin_port));

    snprintf(buffer, sizeof buffer, "%s%s\r\n\r\n",
             gScaryMsg, gHostNameBuf);
    write (acceptSock, buffer, strlen(buffer));

    /*
     * Add newly accepted socket to the active set.
     */
    FD_SET (acceptSock, &gActive_fd_set);
    gMaxFd = MAX(gMaxFd, acceptSock);

    gSockTime[acceptSock] = time(NULL);
    gNumberClients++;
}

/* ------------------------------------------------
 *                                  processSockets 
 * ------------------------------------------------
 */
void processSockets (fd_set   *pRead_fd_set)
{
    int                activeSock;

    /* Service all the sockets with input pending. */
    for (activeSock = 0; activeSock <= gMaxFd; ++activeSock)
    {
        if (FD_ISSET (activeSock, pRead_fd_set))
        {
            if (activeSock == gTcpListenSock)
            {
                /*
                 * Accept a connection for a TCP socket.
                 */
                acceptNewSock ();
            }
            else if (activeSock == gUdpSock)
            {
                /*
                 * Echo data arriving on the UDP socket.
                 */
                echoUdp (activeSock);
            }
            else
            {
                /*
                 * Echo data arriving on a connected TCP socket.
                 */
                echoTcp (activeSock);

            }           /* if (activeSock == gTcpListenSock)        */
        }               /* if (FD_ISSET (activeSock, pRead_fd_set)) */
    }                   /* for (activeSock = 0; ...)                */

}

/* ------------------------------------------------
 *                                        mainLoop 
 * ------------------------------------------------
 */
void mainLoop (void)
{
    int             selectResult;
    fd_set          read_fd_set;
    struct timeval  selectTimeout;
    struct timeval *pSelectTimeout;

    /* Create the tcp socket and set it up to accept connections. */
    gTcpListenSock = bindToPort (SOCK_STREAM);
    if (listen (gTcpListenSock, MAX_QUEUED_CONNS) < 0)
    {
        SYSLOG (LOG_USER, "listen failed");
        exit (EXIT_FAILURE);
    }

    gUdpSock = bindToPort (SOCK_DGRAM);

    /* Initialize the set of active sockets. */
    FD_ZERO (&gActive_fd_set);
    FD_SET (gTcpListenSock, &gActive_fd_set);
    FD_SET (gUdpSock,       &gActive_fd_set);

    gMaxFd = MAX(gTcpListenSock, gUdpSock);
    gNumberClients = 0;

    while (1)
    {
        if ((gMaxSockIdle > 0) && (gNumberClients > 0))
        {
           /*
            * If there are any clients connected, we'll have
            * select timeout every so often so that we can
            * check for idle sockets and close them if they
            * have been idle too long.
            */
           selectTimeout.tv_usec =  0;
           selectTimeout.tv_sec  = 61;
           pSelectTimeout = &selectTimeout;
        }
        else
        {
            /*
             * If there are no clients, or the timeout is disabled,
             * we let select block until there is activity on the
             * listen socket.
             */
            pSelectTimeout = NULL;
        }

        read_fd_set = gActive_fd_set;

        /* Block until input arrives on one or more active sockets. */
        selectResult = select (gMaxFd+1, &read_fd_set, NULL, NULL, pSelectTimeout);

        if (selectResult < 0)
        {
            SYSLOG (LOG_USER, "select failed");
            exit (EXIT_FAILURE);
        }

        if (selectResult > 0)
        {
            processSockets (&read_fd_set);
        }

        if ((gMaxSockIdle > 0) && (selectResult >= 0))
        {
            /*
             * Data received or select timed out.
             */
            checkIdleSockets ();
        }
    }                           /* while (1)    */

    /* not reached */
}

/* ------------------------------------------------
 *                                          usage
 * ------------------------------------------------
 */
void usage (const char *progname)
{
    fprintf (stderr, "%s\n", gVersion);
#ifdef __CYGWIN__
    fprintf (stderr, "\nusage: %s [-adhlpt]\n", progname);
#else
    fprintf (stderr, "\nusage: %s [-adhpt]\n", progname);
#endif
    fprintf (stderr, "      -a <inetaddr>   set local address for bind\n");
    fprintf (stderr, "      -d              enable debug logging\n");
    fprintf (stderr, "      -h              print this help\n");
#ifdef __CYGWIN__
    fprintf (stderr, "      -l <logfile>    log to file <logfile> (default: %s)\n",
             gLogFilename);
#endif
    fprintf (stderr, "      -p #            set port for bind (default: %d)\n", PORT);
    fprintf (stderr, "      -t #            "
                     "set idle socket timeout in minutes (default: %d)\n"
                     "                      zero disables timeout\n\n",
                     MAX_SOCK_IDLE);
}

/* ------------------------------------------------
 *                                          main
 * ------------------------------------------------
 */
int main (int argc, char *argv[])
{
    char            ch;
    char           *progname;
    int             i;
    char            cmdLine[256];
    int             cmdIdx;

    /*
     * Trim path from program name.
     */
    progname = rindex (argv[0], '/');
    if (progname == NULL)
    {
        progname = argv[0];
    }
    else
    {
        progname++;
    }

    /* Set default socket name. */
    gServerName.sin_family      = AF_INET;
    gServerName.sin_port        = htons (PORT);
    gServerName.sin_addr.s_addr = htonl (INADDR_ANY);

    // Log the exact command line used to start the program.
    cmdIdx = 0;
    cmdIdx += sprintf(&cmdLine[cmdIdx], "# %s", progname);
    for (i=1; i<argc; i++)
    {
        cmdIdx += sprintf(&cmdLine[cmdIdx], " %s", argv[i]);
    }

    /*
     * Process cmd line options.
     */
#ifdef __CYGWIN__
    while ((ch = getopt (argc, argv, ":dhl:a:p:t:")) != -1)
#else
    while ((ch = getopt (argc, argv, ":dha:p:t:")) != -1)
#endif
    {
        switch (ch)
        {
        case 'h':
            usage (progname);
            exit (0);
            break;

        case 'd':
            gDebug = 1;
            break;

        case 'a':
            if (strcmp (optarg, "localhost") == 0)
            {
                gServerName.sin_addr.s_addr = htonl (INADDR_LOOPBACK);
            }
            else
            {
                gServerName.sin_addr.s_addr = inet_addr (optarg);
                if (gServerName.sin_addr.s_addr == htonl (INADDR_NONE))
                {
                    fprintf (stderr, "Bad bind address: %s\n", optarg);
                    exit (-1);
                }
            }
            break;

        case 'p':
            {
                uint16_t        port = atoi (optarg);

                if (port < 1024)
                {
                    fprintf (stderr, "Can't bind to privileged port: %hu\n",
                             port);
                    exit (-1);
                }
                gServerName.sin_port = htons (port);
            }
            break;

        case 't':
            gMaxSockIdle = atoi (optarg) * SECS_PER_MIN;
            if (gMaxSockIdle < 0)
            {
                fprintf (stderr, "Error: invalid timeout value\n");
                exit (-1);
            }
            break;

#ifdef __CYGWIN__
        case 'l':
            strncpy (gLogFilename, optarg, sizeof gLogFilename);
            break;
#endif

        default:
            fprintf (stderr, "\nUnknown option");
            usage (progname);
            exit (-1);
            break;
        }
    }

    /*
     * Close all open file descriptors.
     */
    close (STDIN_FILENO);
    close (STDOUT_FILENO);
    close (STDERR_FILENO);

    /*
     * Fork to detach from shell.
     */
    if (fork () != 0)
    {
        exit (0);               /* parent exits */
    }

    SYSLOG (LOG_USER, cmdLine);
    SYSLOG (LOG_USER, "%s : port %hu",
            gVersion, ntohs (gServerName.sin_port));
    if (gDebug)
    {
        SYSLOG (LOG_USER, "Timeout = %d secs; local addr = %s", gMaxSockIdle,
                inet_ntoa (gServerName.sin_addr));
    }

    mainLoop ();                /* does not return */

    exit (0);
}

```

---

### Post by dwhitney67 on 2009-07-26
Um, what's the problem, again?  You were not too clear in your OP.

Btw, the variables similar to the following are not initialized correctly; either you want to initialize them to a null-string, or NULL.  I suspect you want the latter (based on the code I saw).  When initializing a char-pointer to a string, you should declare the char-pointer as const.

So, the following:
```

   char *col1 = "";
   char *col2 = "";
   char *col3 = "";
   ...

```

Should be:
```

   char *col1 = 0;
   char *col2 = 0;
   char *col3 = 0;
   ...

```

Also, although they are similar, most folks tend to use recv() and send() versus using read() and write() when receiving/sending data over a socket.

---

### Post by stuffradio on 2009-07-26
Hi,

the problem is every time someone connects to the socket server... it inserts the database info and then it shuts the socket server down. If possible, I'm trying to find how to keep it from shutting down.

---

### Post by slavik on 2009-07-26
does it shut down when someone connects or does it shutdown after disconnecting? maybe there is a loop that you took out.

---

### Post by dwhitney67 on 2009-07-27
I would look into your usage of this type of statement:
```

for (sock = 0; sock <= gMaxFd; ++sock)
{
   ...
}

```
When a client disconnects you do not update gMaxFd.  When a client connects you do, however you do not account for the fact that there might be gaps in file (socket) descriptors that you are managing.

Consider maintaining a list, or other type of container, to store your socket descriptors.

Equally worthy of mentioning is that the use of global variables is not indicative of a good design.

Try to modularize/organize your code such that you do not have functions performing two or more tasks.

The last thing I would recommend is that you debug the program, and place breakpoints at each location you call close(); determine if you are somehow mistakingly closing the TCP socket.

---

