---
title: "Shared memory shmat() fails with illegal seek"
date: 2009-05-19
forum: Programming Talk
---

### Post by ittiam on 2009-05-19
I created a shared memory and creator process is successfully attached to the shared memory.

However when another process tries to attach itself to the shared memory, it throws an illegal seek error.

Googling told me about shmaddr and SHM_RND as how some system might reject an address of 0, but I am really not clear with that. When the creator process can succssfully attach itself to the shared memory why cant some other process ?

---

### Post by dwhitney67 on 2009-05-19
It would be more helpful if you would post your code, indicating how you created the shared-memory segment, and how your client application is attempting to attach to it.

---

### Post by ittiam on 2009-05-20
Will do so. But can do it only tomorrow.

---

### Post by ittiam on 2009-05-20
Here you go...the code. The error part is highlighted in red.

```

int SHM()
{
   key_t key = ftok(SHM_KEY_PATH,SHM_KEY_ID_1);
 
   if(sender)
      CreateSHM(key);
   else
      AccessSHM(key);
.....
.....
}

```
```

int CreateSHM(key_t key)
{
   int shmId = 0;
   int *sharedSpace = NULL;
   int *sharedSpaceStart = NULL;


   if((shmId = shmget(key, 256, IPC_CREAT | 0660)) < 0)
   {
      printf("%s:Cannot create shared memory %d",__func__, key);
      return -1;
   }

   if((sharedSpace = (int *)shmat(shmId, NULL, 0)) == (int *)-1)
   {
      printf("%s:Cannot attach shared memory %d",__func__, key);
      return -1;
   }
   sharedSpaceStart = sharedSpace;
......
......
......
}

```

```

int AccessSHM(key_t key)
{
   int shmId = 0;
   int *sharedSpace = NULL;
   int *sharedSpaceStart = NULL;

   if((shmId = shmget(key, 256, 0660) == -1))
   {
      printf("%s:Cannot access shared memory %d",__func__, key);
      return -1;
   }
[COLOR="Red"]
   if((sharedSpace = (int *)shmat(shmId, (void *)0, 0)) == (int *)-1)
   {
      perror("shmat");
      printf("%s:Cannot attach shared memory %d, %s",__func__, key,
            strerror(errno));
      return -1;
   }[/COLOR]
......
......
......
}

```

---

### Post by dwhitney67 on 2009-05-20
I compared your code against a sample that I have, and the only difference is your use of ftok(), which you appear to use correctly.

Since you did not offer in your post the definitions of SHM_KEY_PATH or SHM_KEY_ID_1, nor did you define 'sender', I can only assume these are valid values.

I've attached to this post a tar-ball with a couple of files I had saved from a previous stab at using shared-memory.  Perhaps they can help you.

---

### Post by ittiam on 2009-05-21
I really think it is some permission issue. Because when I do ipcs -a, I see the shared memory created by the sender and I can see nattch to 1. So the sender has created and attached itself to the shm successfully. But the other procees just spits out illegal seek every time. At the same time I really dont know what the permission issue could be. 660 is a valid flag for this setting. Clueless.

---

### Post by dwhitney67 on 2009-05-21
Permissing 0660 is the equivalent of rw-rw----.  If you are running both the creator and the client under the same user, then there should not be a problem.  If however, you are running the client under a different user id, and that user id is not part of the group that the creator belongs to, then there is no way for the client to attach to the segment.

Try repeating rerunning your app, but with the mode set to 0666.  (yep, looks evil!)

---

