---
title: "GNOME Keyring: Getting junk data while storing and accessing key"
date: 2011-11-19
forum: Programming Talk
---

### Post by piyush.kansalx on 2011-11-19
Hi,

I need some directions on the following. Please guide me through it:
**Objective:**
To  store and access file encryption keys for a given user. Each file will  have a separate encryption key. So, a user who wants to encrypt 10 files  will have 10 different keys stored on the keyring.

**Issue:** I am facing two issues:
1. Getting junk data while storing and accessing keys
2. Callback function is not being called

**Implementation:**```
#include <stdio.h>
#include <gnome-keyring-1/gnome-keyring.h>
#include <gnome-keyring-1/gnome-keyring-memory.h>

GnomeKeyringPasswordSchema my_schema = {
    GNOME_KEYRING_ITEM_GENERIC_SECRET,
    {
        { "user", GNOME_KEYRING_ATTRIBUTE_TYPE_STRING },
        { "file", GNOME_KEYRING_ATTRIBUTE_TYPE_STRING },
        { NULL, 0 }
    }
};

void
stored_password (GnomeKeyringResult res, gpointer user_data)
{
    printf( "DEBUG: StoredPass - BFR\n" );

        /* user_data will be the same as was passed to gnome_keyring_store_password() */
        if (res == GNOME_KEYRING_RESULT_OK)
                printf ("password saved successfully!\n");
        else
                printf ("couldn't save password: %s", gnome_keyring_result_to_message (res));

    printf( "DEBUG: StoredPass - AFR\n" );
}

void
save_my_password()
{
    GnomeKeyringResult res;
    gpointer gp = NULL, gp2 = NULL;

    printf( "DEBUG: SaveMyPass - BFR\n" );

        gp = gnome_keyring_store_password ( &my_schema,         /* The password type */
                                          GNOME_KEYRING_DEFAULT,          /* Where to save it */
                                          "My file encryption password",    /* Password description, displayed to user */
                                          "test1000",                     /* The password itself */
                                          stored_password,                /* A function called when complete */
                                          gp2, NULL,                        /* User data for callback, and destroy notify */

                                          /* Attributes */
                                          "user", "piyush",
                    "file", "abc.txt",
                                          NULL);                 /* Always end with NULL */

    printf( "DEBUG: SaveMyPass - AFR\n" );

    g_assert( gp != NULL );
    printf( "%p %s\n", gp, (char *)gp );
}

/* A callback called when the operation completes */
void
found_password (GnomeKeyringResult res, const gchar* password, gpointer user_data)
{
        /* user_data will be the same as was passed to gnome_keyring_find_password() */
    printf( "DEBUG: FoundPass - BFR\n" );

        if (res == GNOME_KEYRING_RESULT_OK)
                printf ("password found was: %s\n", password);
        else
                printf ("couldn't find password: %s", gnome_keyring_result_to_message (res));

        /* Once this function returns |password| will be freed */
    printf( "DEBUG: FoundPass - AFR\n" );
}

void
find_my_password()
{
    printf( "DEBUG: FindMyPass - BFR\n" );

        gpointer gp = gnome_keyring_find_password ( &my_schema,      /* The password type */
                                         found_password,                 /* A function called when complete */
                                         NULL, NULL,                     /* User data for callback, and destroy notify */

                                          /* Attributes */
                                          "user", "piyush", 
                                          "file", "abc.txt",
                                     NULL);                 /* Always end with NULL */

    printf( "DEBUG: FindMyPass - AFR\n" );
    g_assert( gp != NULL );
    printf( "%p %s\n", gp, (char *)gp );
}

int main() {
    save_my_password();
    find_my_password();
}


```**Compile:** gcc gnomekey.c -o gnomekey -lgnome-keyring `pkg-config --cflags --libs gnome-keyring-1`
**Output:** ./gnomekey 
DEBUG: SaveMyPass - BFR
DEBUG: SaveMyPass - AFR
0x8676800 <junk-data>
DEBUG: FindMyPass - BFR
DEBUG: FindMyPass - AFR
0x8676828 <junk-data>[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

---

