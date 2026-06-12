---
title: "GUI framework suggestion"
date: 2017-07-17
forum: Programming Talk
---

### Post by 4l3x2 on 2017-07-17
Good morning.

I want to choose a multi platform framework to build my programs. 
I'd like to have these characteristics: -
 - in C++  
- free for every use
 - modular and very bare, skinny, in order to have little/fast executables and just the very minimum functions to learn
 - possibly easy to learn
If it can be helpful I can think of SFML+very basic functions to create a GUI, for now I need to program little games for fun (tetris, samegame...) and simple clients to connect to a database (tipically PostGreSql) to view and edit data, something like Masks and Reports in Access.

I watched for Qt, but it is very big, Gtk is not well supported for Windows (I'll write my programs on Linux, at home, but the users will work on Win in office), Sfml, as stated before, doesn't support GUI creation functions.

I didn't read enough of other frameworks, I know they exist; if you think that would be better to learn 2 little frameworks instead of 1 it's ok, ie: learn Sfml for the low level functions like reading Keys, tracing lines etc... and wxWidgets for creating menus, buttons, folders views etc...
If wxWidgets can be enough for all I need, it seemed to me it is quite well documented and not as big/fat/oversized as Qt, but I can go wrong, obviously.

Thank you very much in advance.

---

### Post by TheFu on 2017-07-17
I don't think anything meets your requirements. wx is the closest, provided the license is ok for your needs.

What about having users run the program on a central system and just have the GUI show up on their desktop?  This way the per-user CPU and RAM requirements become much less.  Of course, it won't work if the users need to be disconnected, but since you mentioned a DBMS, sounds like that isn't the case.

---

### Post by 4l3x2 on 2017-07-17
You are right, the users have to be connected, but hardware requirements aren't an issue.
I'm not sure to understand what you said, however, my initial idea was to install on the server only PG and every user could install the program which connects to the server, retrieves data and displays them on the screen, the management of access on the database is completely done by PG, your proposal can be of 2 types:
- on the server is installed a management software and every user has installed a client software which communicates with the database indirectly and contains the GUI
- on the server is installed a complex software which communicates directly with the database, contains the GUI and every user doesn't have installed anything; each one asks the server for some sort of 'thread' and displays only his dedicated thread (if I understand right is something like cloud computing, the software only runs on the server)

None of the 2 are possible on our system due to the (very strict) security policies of our intranet.

Can you make a simple list for me on the capabilities of the frameworks you know?
Something like a matrix, or a list, ie:

FrameW/         Learning curve/            Functionalities /                                 Weight

Allegro           /steep/                        multimedia/                                       quite heavy
Gtk+/              steep/                        GUI/                                                 quite light
Sfml/              quite easy/                  multimedia+network/                         light
Qt/                 steep/                         GUI+mutimedia+everything else/         sumo fighter
wxWidgets/      quite hard/                  GUI+multimedia/                               modular
FLTK/              steep/                         GUI                                                /very light

I don't know if I wrote right, maybe Allegro supports GUI or Sfml is hard to learn, it's just a list of the cross-platform frameworks of which I know the name and read something around.
For now I'm concentrating on GUI, so we can consider gaming a plus, not a mandatory requirement.
A good plus can be networking functions to connect to the remote database, if they aren't included in standard libraries or in the programming facilities provided by PG (if I remember right every major RDBMS provides the needed library to interact with the database....).

Thank you very much again :)

---

