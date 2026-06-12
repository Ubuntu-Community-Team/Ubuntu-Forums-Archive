---
title: "Newbie Guide: VIM and g++"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by wenjuan on 2013-03-01
i had installed sudo apt-get install vim and g++. On terminal i try out vim helloworld.cpp then pop out the vim edditor then i press I for insert and key in following code:

#include<iostream>
using namespace std;

main()
{
    cout<<"Hello World!"<<endl;
    return 0;
}
ESC Clrl ZZ and go back terminal i type g++ helloworld.cpp -o helloworld.cpp
error failed to create(permision denied)

Help needed

---

### Post by Impavidus on 2013-03-01
I see two problems with what you did. First, you close vim with esc ctrl ZZ. Escape takes you to command mode, ctrl-z will pause vim and return you to your shell without saving your file. You can resume vim with the **fg** command. The correct way of saving and closing vim is shift-ZZ.

Next you compile with **g++ helloworld.cpp -o helloworld.cpp**, which will try and compile helloworld.cpp and save the resulting binary under the same name, overwriting your source code. This is probably not what you want, so you'd better change or remove that extension after the -o.

However, neither of these give the same error message as you recieved. Can you check the permissions and owner of the cpp file using **ls -l helloworld.cpp**?

---

