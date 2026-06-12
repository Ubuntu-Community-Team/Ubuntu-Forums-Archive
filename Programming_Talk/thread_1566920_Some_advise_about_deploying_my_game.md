---
title: "Some advise about deploying my game"
date: 2010-09-03
forum: Programming Talk
---

### Post by redeyerulk on 2010-09-03
Hi,
I have game in development and would like it to be deployed on ubuntu for testing. Game was developed on ubuntu so it works on ubuntu. Now I have Windows deployment chain set up and would like to have the similar on ubuntu. The problem is that my game is in development and it's online game with no single player mode. So as development goes on i need it to be updated almost on the daily bases. On windows I have updater which fetches last version of game binaries and its resources, it also can update itself. I really would like to have something similar on ubuntu.
So I guess I can create .deb package with updater and install it somewhere in ~/.gamename and create a desktop file so user can run it from desktop. Then updater will download the binaries and game resources in the same ~/.gamename folder.
The problem is dependencies. And I have quite a few some of witch are not in ubuntu repositories or build with inappropriate flags. 
If my updater will download also some .so files for my game to use is it a valid way? If for example user have installed some library and then i download my version of .so and put it to the same directory as my game(~/.gamename) will it use my version?

---

### Post by James78 on 2010-09-03
I don't see why it wouldn't be a valid way to download the .so files. If you do it that way, then it's verified by you that it works with your application. That's how I'd do it.. Just remember (making you know just in case) that with every library update you'd need to re-link the executable against it, unless you use dynamic library loading, in which case I think you might not have to rebuild the executable, unless the library breaks it.

---

