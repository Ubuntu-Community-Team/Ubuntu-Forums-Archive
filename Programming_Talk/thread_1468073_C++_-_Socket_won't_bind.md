---
title: "C++ - Socket won't bind"
date: 2010-05-01
forum: Programming Talk
---

### Post by FinalShot on 2010-05-01
I don't know why, but binding fails every time.

```
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <stdio.h>

int main(){
    int sockMain;
    
    printf("Creating socket...\t");
    if ((sockMain = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0){
        printf("Failed to create socket!\n");
        return -1;
    }
    printf("Socket created!\n");
    
    printf("Binding socket...\t");
    sockaddr_in info;
    info.sin_family            = AF_INET;
    info.sin_port            = htons(333);
    info.sin_addr.s_addr    = INADDR_ANY;
    if (bind(sockMain, (sockaddr*)&info, sizeof(info)) < 0){
        printf("Failed to bind socket!\n");
        return -1;
    }
    printf("Socket binded!\n");
    
    close(sockMain);
    return 0;
}

```

---

### Post by dwhitney67 on 2010-05-01
Your attempt to bind socket 333 is failing because you are not running the application with sufficient (ie root) privileges.

As a regular user, you are relegated to using port numbers ranging from 1024 to 65535.

P.S.  Once you resolve the issue with a thread, please mark it as solved (including your other thread you started in regards to winsock).

---

### Post by Quikee on 2010-05-01
Also... you write C++ in the title but your example is C.

---

