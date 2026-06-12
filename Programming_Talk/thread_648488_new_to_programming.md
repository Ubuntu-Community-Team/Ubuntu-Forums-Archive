---
title: "new to programming"
date: 2007-12-23
forum: Programming Talk
---

### Post by kool_kat_os on 2007-12-23
How do you make programs like mozilla firefox, yahoo messenger etc...
I am tryung to use python, just not getting it.

---

### Post by Mr.popo on 2007-12-23
Programs like firefox and yahoo instant messenger are programmed by a team or community not by a single person.

---

### Post by speedingbullet on 2007-12-23
Well, Im sortof a noobie programmer myself, but I already have some great advice for you.


Huge programs like Mozilla Firefox are very complex. I can't understand the programming to them myself.

But when you learn to program, you gotta start off with easy stuff. I tried python, its so simple that its hard for me to understand. You should try starting with C, and start off by making simple programs that run in terminal.

Thats what I'm still doing, except I'm now trying out C++, I'm still far from learning how to write GUI applications.

My method for learning more about programming is programming text games, because they seem easy enough in some parts,

---

### Post by kool_kat_os on 2007-12-23
Hi, I just make this : 

[HTML]#include <cstdlib>
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
    cout << "Hello" << endl;
    system("PAUSE");
}
[/HTML]

After I press a button on the 
```
system("PAUSE");
```
What do I put after that make it launch a folder or another application??

---

### Post by kool_kat_os on 2007-12-23
speedingbullet, can you post of of your game's c++ or C codes so I can take a loook at it and learn how to make more games myself. Thanks

---

### Post by speedingbullet on 2007-12-23
its in several files, so Ill just post them here (and its not done either)

cyber_reality.cpp (main file)
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/

#include "cybernetic_reality.h"

int choosegame ()
{
  int gamechoose;
  cin >> gamechoose;

if (gamechoose == 1)
{
  begginning();
}

if (gamechoose == 2)
{
  password();
}

if (gamechoose == 3)
{
  return 0;
}

if (gamechoose == 4)
{
  cout <<"CYBER REALITY: ANARCHY CHRONICLES\n";
  cout <<"Made by Richard B.\n";
  cout <<"The stories of cyber reality is C 2007 Richard Belken & Icepick studios\n";
  cout <<"The game engine however, is free to modify & redistribute.\n";
  sleep(4);
  return 0;
}
}
//------------------------------------------

//--------------------------------------------------------------------------------

int main ()
{
int starchoice;
cout <<"You Ready to play? 1=true 0=false\n";
cin >> starchoice;
if (starchoice == truez)
{
cout <<"_______PROLOUGE__________\n";
sleep(2);
cout <<"Our story doesnt occur too long after our present day.\n";
sleep(2);
cout <<" In the year 2030, mankind is no better off then what it is now\n";
sleep(2);
cout <<" But something ground breaking happens\n";
sleep(2);
cout <<" One man, inspired by a 31 year old anime series\n";
sleep(2);
cout <<" Invents a long eries of somewhat harmless commandable robots\n";
sleep(2);
cout <<" These are aimed at the public, so he makes sure that everything\n";
cout <<" Goes safely.\n";
sleep(2);
cout <<" The robots are quite a big hit, as the concept is to battle other\n";
cout <<" robots commanded by other people, usually 2 VS 2\n";
sleep(2);
cout <<" But his greatest mistake was the fact that he left himself \n";
cout <<" Off guard.\n";
sleep(2);
cout <<" It was christmas eve, at the robots factory\n";
cout <<" The factory workers were finally leaving for christmas night\n";
cout <<" And this man was leaving too.\n";
sleep(2);
cout <<" But then... THEY came...\n";
sleep(2);
cout <<" THEY slaughtered the factory workers\n";
sleep(2);
cout <<" THEY slaughtered this man\n";
sleep(2);
cout <<" THEY took over.\n";
sleep(3);
cout <<".------.  ____   ___  ______   _____   ______   \n";
sleep(1);
cout <<"| .____|  '  '  '  '  | || |  |  __ |  | ___ |  \n";
sleep(1);
cout <<"| |        '  ''  '   | --.'  |  ___'  | ._ '   \n";
sleep(1);
cout <<"| |____.    '    '    | ||'.  | |___   | | ' '  \n";
sleep(1);
cout <<"|______|     |__|     |____|  |_____|  |_|  '_' \n";
sleep(1);
cout <<"      | _RE_      _AL_     _I_      _TY_ |      \n";
sleep(1);
cout <<"______________________________________________  \n";
cout <<"           ANARCHY CHRONICLES                   \n";
cout <<"______________________________________________  \n";
sleep(1);
  cout <<"______________________________________________________________\n";
  cout <<"                                                              \n";
  cout <<"            1. NEW GAME                                       \n";
  cout <<"            2. CONTINUE                                       \n";
  cout <<"            3. QUIT GAME                                      \n";
  cout <<"            4. About game                                     \n";
  
  choosegame ();
}
if (starchoice == falses)
{
cout <<"Alright, Ill wait 3 minutes.\n";
sleep(250);
main();
}

if (starchoice == secret);
{
password();
}
}

```



story.cpp (im working on this at the moment)
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/

//Filename: story.c
//This file includes the entire, effing storyline. Major spoiler warning if you havent beaten the game.

#include "cybernetic_reality.h"

int begginning()
{ 
cout <<" They say I should just move on...\n";
sleep(2);
cout <<" Oh, sorry, I never really did explain myself\n";
sleep(2);
cout <<" My name? Well to be honest I dont really know.\n";
sleep(2);
cout <<" My parents died when I was really young, I do remember them,\n";
sleep(2);
cout <<" but I don't remember the name they gave me.\n";
sleep(2);
cout <<" We used to live in a small town together\n";
sleep(2);
cout <<" But then, 2 kids about my age at the time started acting wierd\n";
sleep(2);
cout <<" Before one of the townsfolk died, he told me\n";
sleep(2);
cout <<" That they had just upgraded their robots to these very unsafe\n";
sleep(2);
cout <<" looking models\n";
sleep(2);
cout <<" Thier parents tried to tke the robots away,\n";
sleep(2);
cout <<" But the unthinkable happened, they used the robots to kill\n"; 
sleep(2);
cout <<" Their parents, and soon after starte battling each others robots\n";
sleep(2);
cout <<" in a more destructive way. These new robots were highly destructive\n";
sleep(2);
cout <<" So then the Kids constantly started battling each other, destroying\n";
sleep(2);
cout <<" homes, buildings, and killing people in the process\n";
sleep(2);
cout <<" To them, this is just a game, if you dont restrain your self\n";
sleep(2);
cout <<" for petty means of morality, you'll have more fun.\n";
sleep(2);
cout <<"apparently this wasnt like them at all.\n";
sleep(2);
cout <<"It was if they had changed over night... its a mystery\n";
sleep(2);
cout <<"But I don't care, I want them dead.\n";
sleep(2);
cout <<"Not neccessarilly for revenge, I don't want them taking more innocent\n";
sleep(2);
cout <<"But I can't even get close to them... so I dont even know what to do.\n";
sleep(2);
introduction();
}

int yourbot()
{
cout <<"Those 2 bastards aren't out yet... I guess Ill just take a brief\n";
cout <<"walk down to the old train station... its not like I have anything\n";
cout <<"better to do.\n";
sleep(2);
cout <<"You notice something ususual\n";
cout <<"              ........;;ttttttii  ..iiiitt..\n";
cout <<"              GGKKDDWWLLKKffLLGG  DDLLGGDD\n";
cout <<"              ..EE..LLjjDD  ttttttLL..EE..\n";
cout <<"                ttLLttffDD..GG..DD;;LLjj\n";
cout <<"                  GGttGGffttDDttLLiiGG\n";
cout <<"                  ..KKWWEEKKWWDDDDKK..\n";
cout <<"                    DD,,;;;;;;;;;;EE\n";
cout <<"                    KKDDDDWWEEDDDDKK\n";
cout <<"                    DD  ffKKEEtt  DD\n";
cout <<"                    DDLLff    GGffDD\n";
cout <<"                    DDLL..    iiGGDD\n";
cout <<"                    DDiiDD;;iiEE..DD\n";
cout <<"                    DD  ;;KKLL..  DD\n";
cout <<"                    DD    DD..    DD\n";
cout <<"                    DD    DD..    DD\n";
cout <<"                    DD    DD..    DD\n";
cout <<"                    DD    DD..    DD\n";
cout <<"                    DD    DD..    DD\n";
cout <<"                    DD    DD..    DD\n";
cout <<"                    DD    DD      DD\n";
cout <<"                    WWGGjjWWtt;;ttWW\n";
cout <<"                ::DDEEiijjiiiiii;;KKDD;;\n";
cout <<"              ;;EEiiEE            KKiiDDii\n";
cout <<"            iiEEiiEEKK            EEEEiiDDtt\n";
cout <<"          LLGGiiEE::GGii        iiLL..DDttGGGG\n";
cout <<"          WWEEEE..  iiGG        GG;;  ..DDKKKK\n";
cout <<"        ..GGfftt      DD..    ..DD      ttLLGG\n";
cout <<"        ::LLLLii      jjff    LLtt      iiLLLL,,\n";
cout <<"        ;;LLLLii      ..DD    EE..      iiGGLL;;\n";
cout <<"ttffffffLL||||GGffffffffKKLLLLWWLLLLLLLLDD||||GGLLLLLLfffffffffffffffffffff\n";
cout <<"                                                                             ";
yourbotdec();
}

int botintro
{
cout << "I gotta investigate this...\n";
sleep(2);
cout << "You come up closer, the door opens up and you see a robot\n";
cout << "This robot is very small, his weapon seems to be an ordinary house key";
cout << "
}

```



decisions.cpp
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/
#include "cybernetic_reality.h"

int yourbotdec()
{
int choice;
int ready;
cout <<"want to get a bit closer? 1=true 0=false 4=help";
cin >> choice;
if (choice == truez)
{
cout <<"Coming soon!\n";
return 0;
}

if (choice == falses)
{
cout <<"You know, maybe I should think this one through... that IS one stange object..\n";
sleep(250);
cout <<"Are you ready yet?\n";
cin >> ready;

}

if (choice == secret)
{
cout <<"Passwords cant be used here\n";
yourbot();
}

if (choice == 7)
{
cout <<"You just found an easter egg";
}
else
cout <<"Huh? Um.. try again..";
yourbot();

}

```



help.cpp ( I havent been working on this one, but Ill definably get to it.)
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/
//Filename: help.c 

#include "cybernetic_reality.h"


int introduction()
{
cout <<"Hello, allow me to break the fourth wall for a minute\n";
sleep(3);
cout <<"I am this games AI, its my job to guide you through the game!\n";
sleep(3);
cout <<"just type help whenever you need me! I can give you hints when your stuck as well!\n";
sleep(3);
cout <<"Unfortunatly, I cant answer every question, as im mainly composed\n";
sleep(3);
cout <<"of cout statements, so for your convience, the programmer has\n";
sleep(3);
cout <<"set me up a list of questions you can ask me!\n";
sleep(3);
cout<<"                                             \n";
sleep(3);
cout<<"But for now, I would like to explain a feature.\n";
sleep(3);
cout<<"Once I leave, you will see an exploration screen, select one of the\n";
sleep(3);
cout<<"Just select a location! Its that simple! :P\n";
sleep(3);
cout<<"LEAVING AI\n";
sleep(3);
cout<<"Also, your password is: 290456\n";
locmokane();
}

```

password.cpp (ill be deleting this sometime)
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/

#include "cybernetic_reality.h"

int password()
{
int password;

cout<<"Enter your special password\n";
cin >>password;

if( password == passmokane )
locmokane();

else
return 0;
}

```

explore.cpp
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/
#include "cybernetic_reality.h"

int locmokane()
{
int locchoose;
cout <<"STARTER LOCATION: Mokane    \n";
cout <<"former home of the Bulldogs \n";
cout <<"___________________________ \n";
cout <<"                            \n";
cout  <<" Were would you like to go? \n";
sleep(4);

cout <<"1. The Old train Station\n";
cout <<"2. The ruins of Callaway Bank\n";
cin >> locchoose;

if (locchoose == 1)
{
// If you picked one, lets go to the old train station!
yourbot();
}

if (locchoose == 2)
{
cout <<"comingsoon\n";
}
}


```


And finally, the custom header file I made for this program:
```

/***************************************************************************
 *   Copyright (C) 2007 by Richard Belken,,,   *
 *   richard@Shade   *
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 *   This program is distributed in the hope that it will be useful,       *
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         *
 *   GNU General Public License for more details.                          *
 *                                                                         *
 *   You should have received a copy of the GNU General Public License     *
 *   along with this program; if not, write to the                         *
 *   Free Software Foundation, Inc.,                                       *
 *   59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             *
 ***************************************************************************/
#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <iostream>
#include <cstdlib>

// I just looove the sleep() statement
#ifdef HAVE_UNISTD_H
#include <unistd.h>
#endif

// Buuut Micro$oft Windows uses this in a different file
// This windows file contains the Sleep() statement
#ifdef HAVE_WINDOWS_H
#include <windows.h>
#endif

using namespace std;
extern int yourbot();
extern int begginning();
extern int password();
extern int introduction();
extern int yourbotdec();
unsigned int sleep(unsigned int seconds);


extern int locmokane();

// Surely these will be used somewhere....
#define truez              1
#define falses             0
#define secret             3
#define help               4

//_______________________________________________
// These are for password.cpp
#define passmokane        290456

```

I wouldnt recommend taking this to heart, as im not done with it, and I still need to add alot of comments in the source code (those // things)

---

### Post by Kadrus on 2007-12-24
Making a browser similar to Firefox is quite optimistic...but and that is a good but...there is a tutorial on how to make a browser using python...a very good tutorial..and a simple browser...
I suggest reading it...and i hope that by the end of the tutorial you will have  made a little browser to be proud of 
Here's the link:
[http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html](http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html)
Good Luck
:)

---

### Post by kool_kat_os on 2007-12-24
thanks for you help!:)

---

