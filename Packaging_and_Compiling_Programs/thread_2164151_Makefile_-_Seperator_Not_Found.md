---
title: "Makefile - Seperator Not Found"
date: 2013-07-30
forum: Packaging and Compiling Programs
---

### Post by GXdmWQH on 2013-07-30
Hi all,

My makefile is playing havoc at the minute, I can't seem to work out why. It's telling me "Seperator Not Found" on line 11... I didn't write the makefile, nor do I know the source code thoroughly, but I know a little about C++ on Windows, and a small amount about editing files and what not on Linux. Note that I'm doing this entirely using Putty via a non-GUI Ubuntu distro.

Here is the makefile:

```
noinst_PROGRAMS = theforgottenserver

CXXFLAGS = -pipe -g
AM_CXXFLAGS = $(XML_CPPFLAGS) $(OTSERV_FLAGS) $(LUA_CFLAGS) $(DEBUG_FLAGS)\
$(MYSQL_FLAGS) $(MYSQLPP_FLAGS) $(SQLITE_FLAGS) $(PGSQL_FLAGS) $(PROFILER_FLAGS)\
$(OPTIONAL_FLAGS) -D_THREAD_SAFE -D_REENTRANT -Wall -Wextra -Werror -Wno-strict-aliasing


theforgottenserver_LDADD = $(LUA_LIBS)


if USE_MYSQL
MAYBE_MYSQL = databasemysql.cpp databasemysql.h
endif
if USE_MYSQLPP
MAYBE_MYSQLPP = databasemysqlpp.cpp databasemysqlpp.h
endif
if USE_SQLITE
MAYBE_SQLITE = databasesqlite.cpp databasesqlite.h
endif
if USE_PGSQL
MAYBE_PGSQL = databasepgsql.cpp databasepgsql.h
endif
if LOGIN_SERVER
MAYBE_LOGIN = gameservers.cpp gameservers.h
endif
if OT_ADMIN
MAYBE_OTADMIN = admin.cpp admin.h
endif


theforgottenserver_SOURCES = account.h actions.cpp actions.h $(MAYBE_OTADMIN) \
	allocator.cpp allocator.h baseevents.cpp baseevents.h beds.cpp \
	beds.h chat.cpp chat.h combat.cpp combat.h condition.cpp condition.h \
	config.h configmanager.cpp configmanager.h connection.cpp connection.h \
	const.h container.cpp container.h creature.cpp creature.h \
	creatureevent.cpp creatureevent.h cylinder.cpp cylinder.h database.cpp \
	database.h databasemanager.cpp databasemanager.h $(MAYBE_MYSQL) \
	$(MAYBE_MYSQLPP) $(MAYBE_SQLITE) $(MAYBE_PGSQL) depot.cpp depot.h \
	dispatcher.cpp dispatcher.h exception.cpp exception.h fileloader.cpp \
	fileloader.h game.cpp game.h $(MAYBE_LOGIN) globalevent.cpp globalevent.h \
	group.cpp group.h house.cpp house.h housetile.cpp housetile.h ioban.cpp \
	ioban.h ioguild.cpp ioguild.h iologindata.cpp iologindata.h iomap.cpp \
	iomap.h iomapserialize.cpp iomapserialize.h \
	item.cpp item.h itemattributes.cpp itemattributes.h items.cpp items.h \
	luascript.cpp luascript.h mailbox.cpp mailbox.h manager.cpp manager.h \
	map.cpp map.h monster.cpp monster.h monsters.cpp monsters.h \
	movement.cpp movement.h networkmessage.cpp networkmessage.h \
	npc.cpp npc.h otpch.h otserv.cpp otsystem.h outfit.cpp outfit.h \
	outputmessage.cpp outputmessage.h party.cpp party.h player.cpp player.h \
	position.cpp position.h protocol.cpp protocol.h protocolgame.cpp \
	protocolgame.h protocolhttp.cpp protocolhttp.h protocollogin.cpp \
	protocollogin.h protocolold.cpp protocolold.h quests.cpp quests.h \
	raids.cpp raids.h scheduler.cpp scheduler.h scriptmanager.cpp \
	scriptmanager.h server.cpp server.h spawn.cpp spawn.h spells.cpp \
	spells.h status.cpp status.h talkaction.cpp talkaction.h teleport.cpp \
	teleport.h templates.h textlogger.cpp textlogger.h thing.cpp thing.h \
	tile.cpp tile.h tools.cpp tools.h town.h trashholder.cpp trashholder.h \
	waitlist.cpp waitlist.h waypoints.h weapons.cpp weapons.h vocation.cpp \
	vocation.h

```

Any help is appreciated, thanks!

---

### Post by TheFu on 2013-07-30
Makefiles are tab sensitive, so if you opened it with an editor that replaces tabs with spaces, you've screwed the makefile already.

Look for a tutorial on Make and Makefiles to learn about the tab use and be certain you set your editor to leave tabs alone and to leave spaces alone too.

Also, be certain that no MS-DOS crlf are used. Makefiles need UNIX-style end-of-line characters.

If these ideas don't help, please write back with more details. I doubt that copy/paste into this forum will leave the source makefile unmolested, so I didn't bother looking for specific bad characters at the end of lines either.

---

### Post by GXdmWQH on 2013-07-31
> **TheFu said:**
> Makefiles are tab sensitive, so if you opened it with an editor that replaces tabs with spaces, you've screwed the makefile already.

Look for a tutorial on Make and Makefiles to learn about the tab use and be certain you set your editor to leave tabs alone and to leave spaces alone too.

Also, be certain that no MS-DOS crlf are used. Makefiles need UNIX-style end-of-line characters.

If these ideas don't help, please write back with more details. I doubt that copy/paste into this forum will leave the source makefile unmolested, so I didn't bother looking for specific bad characters at the end of lines either.

Thanks for your reply - I can confirm that all of the tabs are still tabs, and the editor I use (ST2) tends to keep the tabs as tabs. I've only actually edited the original using nano via Putty, and that is still behaving correctly regarding tabs at least.

The error displaying on line 11 suggests that this line needs to be indented:

```
MAYBE_MYSQL = databasemysql.cpp databasemysql.h
```

As far as I'm aware, there is no requirement to indent after if statements in Makefiles?

I'm very curious as to end line characters though... I did manage to convince the compiler at one point to tell me that it was expecting "then" at the end of each line beginning with if statement (similar to Lua format, really), so I presume this is not the same error...?

Thanks for your time

---

