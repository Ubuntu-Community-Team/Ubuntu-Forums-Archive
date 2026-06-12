---
title: "Moving file from hugetlbfilesystem to normal filesystem"
date: 2011-07-05
forum: Programming Talk
---

### Post by farazk on 2011-07-05
Suppose hugetlbfs file system is mounted at /mnt/huge.

> const char* from_file = "/mnt/huge/check.txt"; // this file exists
const char* to_file = "./all_logs/check.txt";

const char* from_file1 = "./all_logs/check1.txt"; // this file exists
const char* to_file1 = "./all_logs/check2.txt";



rename(from_file1,to_file1). // it is working
rename(from_file,to_file). // it fails with error message as "Unknown error"
Can someone suggest me a reason for the same and a possible way to do the failing task
in c/c++ without using system() function call.

NOTE : uname -a prints "Linux faraz-laptop 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux"

---

### Post by conradin on 2011-07-05
Im not particularly familiar with hugetlbfs. Are you trying to copy a single file? or someDir? I assume the hugetlbfs can be read by your linux system.

What FS are you moving to? Does the new FS have support for the Files youre trying to move? For Example: FAT Files must be under 4GB. 
EXT2: Cant copy syslinks...

Does it give an error code number?


```

sudo cp -R /mnt/huge /home/User/Desktop 

```

The only way i know to call a bash script in c++ is via the system call.

---

### Post by farazk on 2011-07-05
Yes, I am moving a single file as the c-string file names suggest. Yes hugetlbfs can be read by system that is Ubuntu 10.04. Normal mv command with same parameters as in the failed rename() function call works perfectly fine. I am moving to ext4 file system and file is just 4 MB of size.  And as mentioned in my earlier post, strerror(errno) gives "Unknown error".  I am looking to move file via c/c++ API, I don't want to do it via script, that will take whole lot of time.  Moreover, you have suggested cp command which is not my interest. My interest is moving file, because in this just adjustment of some pointers are done while in cp whole lot of memory is copied.

Thansk for your reply, let me know if there is anything needed for clarification.

---

### Post by psusi on 2011-07-05
You can not rename() across filesystems.  If you want to move a file between filesystems, then you have to copy it and unlink() the original.

---

### Post by conradin on 2011-07-05
I mentioned cp because I see a bunch of other people getting weird errors when they try mv. 
what about a fileIO type deal? Read from some place, write to some other place. No system call. 
```

// reading a text file
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main () {
  string line;
  ifstream myfile ("list3");
  ofstream fout ("list4");
  if (myfile.is_open())
  {
    while ( myfile.good() )
    {
      getline (myfile,line);
      cout << line << endl;
      fout << line << endl;
    }
    myfile.close();
    fout.close();
  }

  else cout << "Unable to open file"; 

  return 0;
}
```

---

### Post by farazk on 2011-07-06
> **conradin said:**
> I mentioned cp because I see a bunch of other people getting weird errors when they try mv. 
what about a fileIO type deal? Read from some place, write to some other place. No system call. 
```

// reading a text file
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main () {
  string line;
  ifstream myfile ("list3");
  ofstream fout ("list4");
  if (myfile.is_open())
  {
    while ( myfile.good() )
    {
      getline (myfile,line);
      cout << line << endl;
      fout << line << endl;
    }
    myfile.close();
    fout.close();
  }

  else cout << "Unable to open file"; 

  return 0;
}
```
@psusi
Then how 'mv' command is working ?

@conradin & psusi
Following is the code I have used for measuring the performance of hard copy and move via system() call :-

> int32_t cpuid = 0;
  cpu_set_t set__;
  CPU_ZERO(&set__);
  CPU_SET(cpuid,&set__);
  sched_setaffinity(getpid(),sizeof(set__),&set__);
  
    void *addr;
  const char* fn__ = "/mnt/huge/check.txt"; 
  const char* nn__ = "./all_logs/check.txt"; 
  
#ifndef TEST_MV  
  int32_t fd = open(fn__,O_RDWR|O_CREAT, S_IRWXU);
  if(fd < 0 ) {
    std::cerr << "unable to open file\n";
    return -1;
  }
  if(ftruncate(fd,LENGTH) < 0) {
    std::cerr << "unable to truncate file\n";
    return -1;
  }

  int32_t to_fd = open(nn__,O_RDWR|O_CREAT, S_IRWXU);
  if(to_fd < 0 ) {
    std::cerr << "unable to open file\n";
    return -1;
  }
  
  addr = mmap(ADDR,LENGTH,PROTECTION,FLAGS,fd,0);
  if(addr == MAP_FAILED) {
    std::cerr << "Unable to mmap file\n";
    return -1;
  }
   
#else  
  std::string command = "mv ";
  command += fn__;
  command += " ";
  command += nn__;
#endif  
  
  clockid_t id;
  clock_getcpuclockid(getpid(),&id);
  struct timespec res;
  struct timespec value1,value2;
  clock_getres(id,&res);
  clock_gettime(id,&value1);  
  
#ifndef TEST_MV  
  write(to_fd,addr,LENGTH) ;
#else  
  system(command.c_str());
#endif  
  clock_gettime(id,&value2);
  int64_t diff1 = value2.tv_sec - value1.tv_sec;
  int64_t diff2 = value2.tv_nsec - value1.tv_nsec;
  std::cerr << "diff = " << diff1 << " : " << diff2 << "\n"; 
  
#ifndef TEST_MV
  munmap(addr,LENGTH);
  close(fd);
  close(to_fd);
#endif  
  
    return 0;I make -O3 static build for performance testing. Process is bound to one cpu to take into account the multiple cpu clock sync problem.

Important points to note :
1) Simple mv command via script is faster that hard copy by around 50 time for 4 MB of file size.
2) As file size increases mv command time remains constant (more or less) but hard copy time increases
with size.

That means 'mv' command is not doing hard copy and the very fact that it is working tells me that there has to be some way to move file using c/c++ API, and of course there is last fall back option, that is, to use system() call. I am looking for c/c++ API because it will be faster as there will be no separate process creation etc. as it happens for system() call.

Is there any other place where this post might be more appropriate ?  Anyone knows where I can post questions specifically related to hugetlbfs ?

---

### Post by johnl on 2011-07-06
Why don't you do the following:

```

strace mv /mnt/huge/check.txt /where/ever/else.txt

```

and see which system calls mv is doing to accomplish this?

Secondly,  I would check the return value of rename() and then errno/perror() as appropriate for more information.

---

### Post by farazk on 2011-07-06
In program it is giving "unknown error". However when I do stack trace as you mentioned above, it gives EXDEV

The stack trace is attached. Point to note is that there is no write to newly created file. Still don't see how to utilize this info.

---

### Post by johnl on 2011-07-06
the strace you posted is from **mv**, right?  Look at what happens:

It tries to call rename(), which fails:
```

rename("/mnt/huge/check.txt", "./check.txt") = -1 EXDEV (Invalid cross-device link)

```

So it falls back to copying the file manually:

```

open("/mnt/huge/check.txt", O_RDONLY|O_NOFOLLOW) = 3
open("./check.txt", O_WRONLY|O_CREAT|O_EXCL, 0600) = 4

```

Followed by quite a few reads() and lseeks() -- you're right in that I don't see a write() call, but it's possible that what it's doing is reading the data from the first file directly into a memory mapped buffer for the second file.

But what I was hoping this would show is that the reason **mv** works but **rename()** doesn't is because mv is handling this condition and falling back to a different method.  This is probably what you should do as well.  You can take a look at the source to mv if you want via:

```

apt-get source coreutils

```

If you want to know more about what it's doing.

---

### Post by farazk on 2011-07-06
And whatever that fall back method is, it seems to be very efficient. I didn't wanted to go through code but it looks like i have no other option left.  Thanks a lot for the help.

---

### Post by psusi on 2011-07-06
> **farazk said:**
> @psusi
Then how 'mv' command is working ?

Like I said before: copy and delete the original.

> **farazk said:**
> 
Important points to note :
1) Simple mv command via script is faster that hard copy by around 50 time for 4 MB of file size.
2) As file size increases mv command time remains constant (more or less) but hard copy time increases
with size.

Only when the source and destination directories are on the same filesystem.  When you try to cross filesystems, it falls back to copy and delete.

---

