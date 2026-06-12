---
title: "Store password into gnome Keyring through the gnome-keyring api"
date: 2008-07-03
forum: Programming Talk
---

### Post by hannehomuth on 2008-07-03
Hi Everyone,

I'd like to ask you a question. I wanna store some pw into the Gnome Keymanger. I use java and I've written a wrapper for the native libary. But when I wanna insert a pw it is not be shown in there. Here some code

```


JNIEXPORT jboolean JNICALL Java_de_sourcepark_ldap_KeyRingConnector_addPasswordToKeyRingManger (JNIEnv *env, jobject obj)
{
    #define false 0
    #define true (!false)

    printf("wanna create pw \n");
    gnome_keyring_store_password(GNOME_KEYRING_NETWORK_PASSWORD,
                                 GNOME_KEYRING_SESSION,
                                 "Mein Ldap Passwort",
                                 "testpw",
                                  stored_password,
                                  NULL,NULL,
                                 "user","jhomuth",
                                 "protocol","ldap",
                                 "domain","localhost",
                                 "port",389,
                                  NULL
);
    
    printf("I sould have created it");
    return true;
}

```

But is not be shown in the mangager. When I type into console gnome-keyring-manager there is only The keyring session shown. Look I at the wrong location ?

---

### Post by Zugzwang on 2008-07-03
I don't have knowledge of Gnome programming, but according to [http://http://library.gnome.org/devel/gnome-keyring/stable/gnome-keyring-gnome-keyring-password.html#gnome-keyring-store-password]("http://http://library.gnome.org/devel/gnome-keyring/stable/gnome-keyring-gnome-keyring-password.html#gnome-keyring-store-password"), the option "GNOME_KEYRING_SESSION" is for storing in memory only. You might want to try NULL instead. Also, did you check how your callback function is called?

---

### Post by hannehomuth on 2008-07-03
Hi I already tried this, but there is the same effect(no effect). My Callback Method did'nt run. Any other ideas

---

### Post by hannehomuth on 2008-07-03
If solved it, I had to use the  gnome_keyring_store_password_sync method, and everything worked fine. wtf!!

---

