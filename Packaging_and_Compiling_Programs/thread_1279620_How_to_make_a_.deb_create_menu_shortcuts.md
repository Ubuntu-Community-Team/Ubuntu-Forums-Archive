---
title: "How to make a .deb create menu shortcuts?"
date: 2009-10-01
forum: Packaging and Compiling Programs
---

### Post by DemonTPx on 2009-10-01
Hi,

Using checkinstall, I've created a .deb for a game I've been working on. Here is my makefile:

```
CC=g++
CFLAGS=-c -Wall
LDFLAGS=-lSDL -lSDL_mixer -lz -lstdc++
SRCS=Airstrike.cpp\
        AirstrikePowerUp.cpp\
        AmmoPowerUp.cpp\
        AudioController.cpp\
        AudioOptions.cpp\
        Bomb.cpp\
        BombPowerUp.cpp\
        CharacterSelect.cpp\
        ChickNPC.cpp\
        ControlsOptions.cpp\
        DoubleDamagePowerUp.cpp\
        GameInput.cpp\
        Gameplay.cpp\
        GameplayObject.cpp\
        Graphics.cpp\
        HealthPowerUp.cpp\
        InstantKillBulletPowerUp.cpp\
        Level.cpp\
        LevelSelect.cpp\
        LocalMultiplayer.cpp\
        LocalMultiplayerRoundEnd.cpp\
        Main.cpp\
        Menu.cpp\
        Mission.cpp\
        NPC.cpp\
        Options.cpp\
        OptionsScreen.cpp\
        PauseMenu.cpp\
        Player.cpp\
        PlayerAnimation.cpp\
        Projectile.cpp\
        Text.cpp\
        Timer.cpp
OBJS=$(SRCS:.cpp=.o)
EXECUTABLE=battle

all: $(EXECUTABLE)

$(EXECUTABLE): $(OBJS)
        $(CC) $(LDFLAGS) $(OBJS) -o battle

.cpp.o:
        $(CC) $(CFLAGS) $< -o $@

clean:
        -rm -rf *.o battle

install:
        mkdir -p /usr/share/games/smashbattle
        cp $(EXECUTABLE) /usr/share/games/smashbattle
        mkdir -p /usr/share/games/smashbattle/gfx
        mkdir -p /usr/share/games/smashbattle/sfx
        mkdir -p /usr/share/games/smashbattle/music
        mkdir -p /usr/share/games/smashbattle/stage
        cp -R gfx/* /usr/share/games/smashbattle/gfx/
        cp -R sfx/* /usr/share/games/smashbattle/sfx/
        cp -R music/* /usr/share/games/smashbattle/music/
        cp -R stage/* /usr/share/games/smashbattle/stage/
        cp smashbattle /usr/local/bin/

```

This works great, but I also want my .deb to install a menu shortcut into the gnome and/or KDE menu. How can I do this?

I've already created two .desktop-files that need to be used.

More about the game here: [devblog]("http://smashbattle.condor.tv") [sourceforge]("http://sf.net/projects/smashbattle")

Thanks!

---

### Post by dinxter on 2009-10-01
.desktop files in 
/usr/share/applications/
should show up in menus
As checkinstall is a helper for using package management with local source and not really a 'proper' deb package i'm not sure how exactly the best way is to go about it. i believe checkinstall wraps around 'make install' so thats probably the section of your makefile to place the cp command in

---

### Post by DemonTPx on 2009-10-01
> **dinxter said:**
> .desktop files in 
/usr/share/applications/
should show up in menus
As checkinstall is a helper for using package management with local source and not really a 'proper' deb package i'm not sure how exactly the best way is to go about it. i believe checkinstall wraps around 'make install' so thats probably the section of your makefile to place the cp command in
Thanks for your reply.

This sounds like a dirty way, but I'll give it a try.  I haven't tried this before because I thought there might be proper way of doing this.
checkinstall indeed wraps around 'make install', that's why I've included the Makefile in my thread start.

---

### Post by dinxter on 2009-10-01
it may look dirty :) but installing/removing .desktop files to that directory is a standard way for debian packages to add themselves to the menu system. its proper I promise!

---

### Post by DemonTPx on 2009-10-01
> **dinxter said:**
> it may look dirty :) but installing/removing .desktop files to that directory is a standard way for debian packages to add themselves to the menu system. its proper I promise!

I just tested it out. The deb-file copies the two .desktop-files to /usr/share/applications, but they don't show up in the menu or the menu editor. So it doesn't work :(.

---

### Post by dinxter on 2009-10-01
i am on karmic i dont know if that makes any difference, i've attached proven working desktop entry, when i copy it to /usr/share/applications it shows up in 'Internet' on my gnome menu. There might be an 'update-menus' command you need to run but its not needed here. what do your .desktop files look like? i take it .desktop-files is a typo and the files are actually end in .desktop

---

### Post by dinxter on 2009-10-01
well, attached it now anyway :)

---

### Post by DemonTPx on 2009-10-05
This is what my smashbattle.desktop file looks like:

```
[Desktop Entry]
Type=Application
Version=1.0
Name=Smash Battle
GenericName=Arcade mutliplayer shooter
Icon=/usr/share/games/smashbattle/gfx/SB.png
Exec=/usr/local/bin/smashbattle
Categories=Game;ArcadeGame;

```

I don't see anything wrong with it... the update-menus command also doesn't change anything...

---

### Post by dinxter on 2009-10-05
strange, i've just copied that .desktop file to /usr/share/applications and it shows up in the menu instantly on karmic

---

