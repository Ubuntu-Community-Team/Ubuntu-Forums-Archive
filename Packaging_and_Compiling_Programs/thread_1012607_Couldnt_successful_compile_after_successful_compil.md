---
title: "Couldnt successful compile after successful compilation"
date: 2008-12-16
forum: Packaging and Compiling Programs
---

### Post by shankhs on 2008-12-16
I was advised by mc4man to post my problem here:
[http://ubuntuforums.org/showthread.php?t=1011926](http://ubuntuforums.org/showthread.php?t=1011926)

My problem is :
I successfully installed SNL([http://www.gnomefiles.org/app.php?soft_id=2205](http://www.gnomefiles.org/app.php?soft_id=2205)) and dependencies like libglib2.0 is pre-installed and so I didnt have any problem so far.
Now to test the installation I ran one of the sample programs here is the code
```

/*
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Library General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA
 */
 
/**** SAMPLE DESCRIPTION ****
 *
 * How this sample work:
 * 1. Create and run TCP client
 * 2. Connect with server
 * 3. Send message
 * 3. Receive message
 * 4. Disconnect and exit
 *
 * This sample shows how to create TCP client and run it using asynchronous
 * interface.
 */

#include <glib.h>
#include <snl.h>
#include <stdio.h>

/*******************************************************************************
    SIGNALS
 ******************************************************************************/
void    connect_signal  (SnlClient  *client,
                         SnlAddress *address,
                         gpointer   user_data)
{
    printf ("Client was connected\n");
    /* Enable auto receiving */
    snl_client_set_auto_receive (SNL_CLIENT (client), TRUE);
    /* Send message to server */
    snl_client_async_send (SNL_CLIENT (client), "Hi! I'm a async client!", 23, 5000000);
}

void    disconnect_signal  (SnlClient  *client,
                            gpointer   user_data)
{
    printf ("Clieant was disconnected\n");
}

void    send_signal     (SnlClient  *client,
                         gpointer   data,
                         gsize      data_len,
                         gpointer   user_data)
{
    printf ("Message: \'%s\' (%d bytes) was sent\n", (gchar *)data, data_len);
}

void    recv_signal     (SnlClient  *client,
                         gpointer   data,
                         gsize      data_len,
                         gpointer   user_data)
{
    printf ("Message: \'%s\' (%d bytes) was received\n", (gchar *)data, data_len); 
}

void    error_signal    (SnlClient  *client,
                         SnlError   *error,
                         gpointer   user_data)
{
    switch (error->error_operation) {
        case SNL_ERROR_OPERATION_CLIENT_CONNECT:
            printf ("Failed to connect, message: %s\n", error->generic_error->message);
            /* For some error SNL provides additional information, this example shows ho to use them properly */
            printf ("Failed to connect address: %s\n", snl_address_get_ip_address (SNL_ERROR_CLIENT_CONNECT (error)->address));
            break;
        case SNL_ERROR_OPERATION_CLIENT_DISCONNECT:
            printf ("Failed to disconnect, message: %s\n", error->generic_error->message);
            break;
        case SNL_ERROR_OPERATION_CLIENT_SEND:
            printf ("Failed to send, message: %s\n", error->generic_error->message);
            /* Another example showing how to use additional information about error */
            printf ("Failed to send this message: %s (%d bytes)\n", SNL_ERROR_CLIENT_SEND (error)->data, SNL_ERROR_CLIENT_SEND (error)->data_len);
            break;
        case SNL_ERROR_OPERATION_CLIENT_RECEIVE:
            printf ("Failed to receive, message: %s\n", error->generic_error->message);
            break;
        default:
            printf ("Unknown error, message: %s\n", error->generic_error->message);
    }
}

void    destroy_signal  (SnlClient  *client,
                         gpointer   user_data)
{
    printf ("Object is being destroyed....\n");
}

/*******************************************************************************
    PROGRAM - 'main' function
 ******************************************************************************/
int main    (void)  {
    SnlTcpClient    *client;
    SnlAddress      *address;
    GError          *error = NULL;
    gboolean        status;

    /* SNL will not work if GType and GThread weren't initialized! */
    g_type_init ();
    g_thread_init (NULL);
    
    /* Now you can initialize SNL */
    status = snl_main_init (&error);
    if (status == FALSE)    {
        printf ("Failed to initialize library, error message: %s\n", error->message);
        g_clear_error (&error);
        return 0;
    }
    
    /* Create new instance of SnlTcpClient type, prepare address and connect signals */
    client = snl_tcp_client_new (SNL_ADDRESS_FAMILY_IPV4);
    address = snl_address_new ("127.0.0.1", 2345);    
    g_signal_connect (SNL_CLIENT (client), "connect", G_CALLBACK (connect_signal), NULL);
    g_signal_connect (SNL_CLIENT (client), "disconnect", G_CALLBACK (disconnect_signal), NULL);
    g_signal_connect (SNL_CLIENT (client), "send", G_CALLBACK (send_signal), NULL);  
    g_signal_connect (SNL_CLIENT (client), "receive", G_CALLBACK (recv_signal), NULL);  
    g_signal_connect (SNL_CLIENT (client), "destroy", G_CALLBACK (destroy_signal), NULL); 
    g_signal_connect (SNL_CLIENT (client), "error", G_CALLBACK (error_signal), NULL); 
        
    /* Connect with server */
    snl_client_async_connect (SNL_CLIENT (client), address, 10000000);
    
    /* Now wait 20 secodns until async tasks complete */
    g_usleep (20000000);
    
    snl_object_destroy (SNL_OBJECT (client));
    snl_address_free (address);
    status = snl_main_finalize (&error);
    if (status == FALSE)    {
        printf ("Failed to finalize library, error message: %s\n", error->message);
        g_clear_error (&error);
    }
    
    return 0;
}

```
I couldnt successfully compile it as it continously says glib.h:no such file or directory.
I think the code didnt compile because glib.h couldnt be included its in glib-2.0 now thats a big problem because glib.h has all the include files in glib-2.0/glib/ so glib.h has to be modified!!!!
what should I do?
Modify glib.h or is there any other way?
Please help.
What I meant was : The basic of C programing tells me that if I am including something in linux it must be in /usr/include isn't it?
but this glib.h is in /usr/include/glib-2.0/ so I must do something like this:
```

#include <glib-2.0/glib.h>

```
Now I figured out that glibconfig.h is in /usr/lib/glib/include/glibconfig.h now how would a C program knows that address? It will unsuccessfully search for /usr/include/glibconfig.h and return an error.
Am I missing something?
Please help me.

---

### Post by geraldm on 2008-12-19
This is usually done in a Makefile where you would only have to enter the location once.

Each header directory needs to be passed as a flag to the compiler if you are
not using a Makefile.

gcc -I/usr/include/glib-2.0 {other compiler info}


Gerald

---

### Post by gmclachl on 2008-12-19
pkg-config is your friend. 

If you run "pkg-config --cflags glib-2.0" from the command line you will see a list of includes. 

When you compile you can do 

 gcc xxxxx.c -o xxxxx `pkg-config --cflags glib-2.0` 

 *note the back ticks not single quotes

 George

---

