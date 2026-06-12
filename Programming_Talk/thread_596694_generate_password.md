---
title: "generate password"
date: 2007-10-29
forum: Programming Talk
---

### Post by dwhitney67 on 2007-10-29
Does anyone know how the clear-text passwords are encrypted before being stored in the /etc/passwd file?  Is there a system utility that I can use within a shell script?

---

### Post by gradedcheese on 2007-10-30
Take a look at "man shadow", especially:

> 
Refer to crypt(3) for details on how this string is interpreted.


and so:

```

man 3 crypt

```

should have the answer...

---

### Post by dwhitney67 on 2007-10-30
Thanks.  While waiting for assistance I did look into crypt(), and found it to be sort of a dead-end.  The API states that the first arg is the clear-text password (key), and the second arg is a "salt" string.  Since I do not know which salt string is used by passwd, I do not know if I am able to generate a similar key.

Here's my code:
[PHP]#define _XOPEN_SOURCE
#include <unistd.h>
#include <string>
#include <iostream>
using namespace std;


int main( int argc, char** argv )
{
  string salt( "foo" );

  if ( argc < 2 )
  {
    cout << "usage: " << argv[0] << " [password] <salt-string>" << endl;
    return 0;
  }
  if ( argc == 3 )
  {
    salt = string( argv[2] );
  }

  cout << "encoded password is: " << crypt( argv[1], salt.c_str() ) << endl;
}[/PHP]

I ran it with the most overused password in the World, "password", and a salt of "LBCT".  The result was:  LBCT7Ou3w//TQ

Any thoughts as to whether my approach has a flaw in it?  I almost believe it does.

****************  

Ha!  Nevermind... I (think) I understand it now.  The salt string represents the first two-characters of the encoded string as it appears in the /etc/passwd file.  Now I clearly understand why shadow passwording (sp?) is recommended.

---

### Post by syssyphus on 2007-10-30
[http://linux.die.net/man/3/crypt](http://linux.die.net/man/3/crypt)

sorry to just post a link, but the system call crypt() is what generates that hash, not sure if there is a pre-packaged binary that will do the job.

---

