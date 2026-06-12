---
title: "qns on pthread and locking"
date: 2011-02-15
forum: Programming Talk
---

### Post by guest_user on 2011-02-15
```


int startServer( struct ServerParameter &serverParameter )
{
    pthread_t threadID;
    ConnectionParameter *connectionParameter;
    SharedData sharedData;
    pthread_mutex_t sharedDataLock;
    int newFD;

    // initialize lock here

    while ( 1 )
    {
        connectionParameter = new ConnectionParameter();
        connectionParameter -> newFD = accept( serverFD, NULL, NULL );

        pthread_mutex_lock( &sharedDataLock );
        connectionParameter -> sharedDataPtr = &sharedData;
        pthread_mutex_unlock( &sharedDataLock );

        connectionParameter -> sharedDataLockPtr = &sharedDataLock; // Do I have to have a lock to this lock too?

        pthread_create( &threadID, NULL, &handleConnection, connectionParameter );
    }
    ...
}


```

In this line,
connectionParameter.sharedDataLockPtr = &sharedDataLock;

Do I have to have a lock to this lock too?

---

### Post by MadCow108 on 2011-02-15
I do not see the need for a lock here at all.
1. pointer assignments are atomic (at least on x86)
2. the "shared" data (the pointer to sharedData) is not shared at the time of the locking

---

### Post by guest_user on 2011-02-15
> **MadCow108 said:**
> I do not see the need for a lock here at all.
1. pointer assignments are atomic (at least on x86)
2. the "shared" data (the pointer to sharedData) is not shared at the time of the locking

the shared data is shared at the time of locking because after creating a thread to handle an existing connection, it may loop back to handle another connection

---

### Post by MadCow108 on 2011-02-15
> **guest_user said:**
> the shared data is shared at the time of locking because after creating a thread to handle an existing connection, it may loop back to handle another connection

yes but this thread gets a completely new ConnectionParameter which does (hopefully) not share the pointer.

The only way I see how there can be locking required is when your ConnectionParameter has a global state which allows a thread handling a connection to spawn another thread which can mess with the data of the parent thread.
and this is really bad design. The ConnectionParameter should be local to the thread.

If you are paranoid just move the line into the lock. The assignment cost is negligible compared to the locking itself, so there is no performance impact compared to the assignment outside of the lock.

---

