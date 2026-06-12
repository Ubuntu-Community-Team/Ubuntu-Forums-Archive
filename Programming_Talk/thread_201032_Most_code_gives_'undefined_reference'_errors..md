---
title: "Most code gives 'undefined reference' errors."
date: 2006-06-21
forum: Programming Talk
---

### Post by fakeh on 2006-06-21
I have recently upgraded breezy to dapper in the automated way. Unfortunately the latest kernel does not boot and gets stuck at loading hald. So I'm still using the 2.6.12-10-386 kernel. Anyway, this seems to have broken gcc's ability to compile code. For a long time I assumed that I was simply writing guff code, however, I began to suspect that there was something wrong with my configuration or that I am now missing some library.

```
#include <iostream>
#include <iomanip>
#include <fstream>
using namespace std;

int main() {
    int sum = 0;
    int x;
    ifstream inFile;
    
    inFile.open("test.txt");
    if (!inFile) {
        cout << "Unable to open file";
        exit(1); // terminate with error
    }
    
    while (inFile >> x) {
        sum = sum + x;
    }
    
    inFile.close();
    cout << "Sum = " << sum << endl; 
    return 0;
}
```

For example (taken from [http://www.fredosaurus.com/notes-cpp/io/readtextfile.html]("http://www.fredosaurus.com/notes-cpp/io/readtextfile.html"))  gives the same sort of errors I was receiving with my own code.

E.g.

```
/tmp/ccExYIui.o: In function `main':tst.cpp:(.text+0x31): undefined reference to `std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream()'
:tst.cpp:(.text+0x4f): undefined reference to `std::basic_ifstream<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode)'
:tst.cpp:(.text+0x62): undefined reference to `std::basic_ios<char, std::char_traits<char> >::operator!() const'
:tst.cpp:(.text+0x75): undefined reference to `std::cout'
```

etc.

I'm guessing that I'm missing some libraries that were upgraded and I need to install backdated packages??

Many thanks for any help provided, 
Dan.

---

### Post by localzuk on 2006-06-21
have you got the build-essential package installed?

---

### Post by fakeh on 2006-06-21
Yes.

---

### Post by thumper on 2006-06-21
it might help for you to show us your sources.list file as the upgrade may have been less than fully successful

---

### Post by fakeh on 2006-06-21
[QUOTE=thumper]it might help for you to show us your sources.list file as the upgrade may have been less than fully successful[/QUOTE]

Here ya go,

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://gb.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu dapper universe main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted

```

---

### Post by thumper on 2006-06-21
hmm... well that looks correct.

Not sure. Sorry.

---

### Post by hod139 on 2006-06-21
Just a guess, but are you using the command gcc to try and compile this code?

You need to use g++ to compile c++ code.

---

### Post by SweetenedCaneSugar on 2008-09-23
fixed my problem <_<

---

### Post by StOoZ on 2008-09-23
you were using gcc instead of g++?

---

