---
title: "Error running java program"
date: 2013-08-13
forum: Programming Talk
---

### Post by P3n6uin on 2013-08-13
Not sure if this is the place to ask but searches on the hardware (Rio Karma) have turned up nothing.
The Riovolution page is out of commission at this time and the error message itself isn't turning up anything that looks useful so I'm hoping someone here can give me a clue.

When I attempt to run Rio Music Manager Lite, I'm getting this error:

Failed to download the music database from the device. caused by:
java.lang.StringIndexOutOfBoundsException: String index out of range: -1

There seems to be no way to rebuild the database that I can see and resetting the device hasn't helped.
Formatting the hd might help but I'd like to avoid that if possible.

The full error message:

Failed to download the music database from the device. caused by:
java.lang.StringIndexOutOfBoundsException: String index out of range: -1
	at java.lang.String.<init>(String.java:197)
	at com.inzyme.util.IgnoreArticlesCollator.putArticleOnEnd(IgnoreArticlesCollator.java:79)
	at com.inzyme.util.IgnoreArticlesCollator.getCollationKey(IgnoreArticlesCollator.java:52)
	at com.inzyme.util.CollationKeyCache.getCollationKey(CollationKeyCache.java:72)
	at com.inzyme.util.CollationKeySortableContainer.getSortValue(CollationKeySortableContainer.java:25)
	at com.inzyme.util.SortUtils.binarySearch(SortUtils.java:125)
	at org.jempeg.music.nodestore.model.AbstractPlaylistContainerModifier.addChild(AbstractPlaylistContainerModifier.java:92)
	at org.jempeg.music.nodestore.soup.AbstractTagSoupUpdater.nodeIdentified(AbstractTagSoupUpdater.java:232)
	at org.jempeg.music.nodestore.soup.AbstractTagSoupUpdater.nodeIdentified(AbstractTagSoupUpdater.java:160)
	at org.jempeg.music.nodestore.soup.SearchSoupUpdater.nodeIdentified(SearchSoupUpdater.java:163)
	at org.jempeg.music.nodestore.soup.SearchSoupUpdater.initialize(SearchSoupUpdater.java:146)
	at org.jempeg.music.nodestore.soup.SoupUtils$SoupInitializeRunnable.run(SoupUtils.java:325)
	at org.jempeg.music.nodestore.soup.SoupUtils.attachSoup(SoupUtils.java:290)
	at org.jempeg.music.nodestore.soup.SoupUtils.createTransientSoupPlaylist(SoupUtils.java:109)
	at org.jempeg.music.nodestore.soup.SoupUtils.createTransientSoupPlaylist(SoupUtils.java:90)
	at org.jempeg.music.nodestore.soup.SoupUtils.createTransientSoupPlaylist(SoupUtils.java:75)
	at com.rio.rmmlite.RioMusicManagerLiteUI.databaseCheckedForProblems(RioMusicManagerLiteUI.java:154)
	at org.jempeg.music.nodestore.PlayerDatabase.fireDatabaseCheckedForProblems(PlayerDatabase.java:343)
	at org.jempeg.music.nodestore.PlayerDatabase.checkForProblems(PlayerDatabase.java:516)
	at org.jempeg.music.manager.EmplodeSyncManager.download(EmplodeSyncManager.java:222)
	at org.jempeg.music.manager.EmplodeSyncManager$2.run(EmplodeSyncManager.java:190)
	at java.lang.Thread.run(Thread.java:724)


Any advice on resolving the issue?
Thanks

---

### Post by TheFu on 2013-08-13
Does the Rio need Oracle's Java or will it work with OpenJDK?

---

### Post by ofnuts on 2013-08-14
Which JRE are you using?

---

### Post by P3n6uin on 2013-08-14
I have JDK Java 7 Runtime

---

### Post by P3n6uin on 2013-08-14
I have two Karmas the other one is accessible with JDK Java 7 and I have used JRE under another Ubuntu version.

---

### Post by TheFu on 2013-08-14
> **P3n6uin said:**
> I have JDK Java 7 Runtime

I'm knew to Java. Is that OpenJDK or Oracle's?
There is a huge difference to many programs.

---

### Post by Boab1993 on 2013-08-14
Usually when an index is out of bounds it tends to suggest that there is either no -or to much- data.

Bounds  are set by the programmer, since yours is a music database, i imagine  it just means it can't find any data in the database, thus throwing an  exception.

Or it is also possible, since its a string, the range '-1' is an invalid type, e.g. not long enough

Fully prepared to be wrong, just a thought.

---

### Post by QIII on 2013-08-14
I'll have to agree with Boab1993.

I don't think this is a Java issue per se, so I don't think we really need to worry about OpenJDK versus Java.  And formatting the HD has nothing to do with it at all.

Look at the exception being thrown.

String indexes run from 0 to (length - 1).  The indexes of the characters of a 5 character string would be 0 to 4.  5 produces an out of range exception, as does -1. 

In this case, the java.lang exception is thrown because the index is -1, which is out of bounds and both OpenJDK and Oracle Java will throw the exception.  That sort of thing can happen if a zero length string is passed and, in determining the upper bound of the indexes to be (length - 1), the result is (0 - 1) or -1.

My suspicion is that this is a bug in the application itself.  Either the developers didn't deal with how to handle a zero-length string gracefully or the application assumes that no zero-length string will be passed -- or both.  If it is a fault in the application, in either case it represents bad programming practice.

If there is a database involved, say MySQL or SQLite, and there is a null or zero-length string in a column where there should not be, then either the data is corrupt, the database was improperly designed or the application is not ensuring that data stored has been properly validated -- or all three. 

If the "database" is actually a flat file, then all bets for anything being worth a plug nickel are off. 

Do you know if this is still under active development?

---

### Post by P3n6uin on 2013-08-15
I hadn't used the app in quite a while but it did work on both Karmas last time I used it - maybe a year ago - and many times before that.
I think it is no longer being developed, latest version is from 2007 or so.
The Karma is a bit of a dinosaur but they both still play music.
Since the program works fine on the other Karma it seems pretty clear the data on the troubled one is probably corrupt - wouldn't nuking it solve the issue?

I Appreciate all the input.

---

### Post by Boab1993 on 2013-08-15
Im not familar with the term nuke, but im going to take it means obliterate or all purpose fix?

If you don't have writing permissions on the database you'd have to contact an admistator of the website and report the bug.

I dont think theres anything you can do from your side as a consumer.

Sorry i cant be more help

---

### Post by P3n6uin on 2013-08-16
I'm not sure what website you're referring to but as for nuke, I'm referring to wiping the hd.
If the data is corrupt this ought to resolve the issue.
Thanks again.

---

### Post by QIII on 2013-08-16
But why on earth would you want to nuke an entire drive to correct a problem with the data for one application?

That's like throwing a hand grenade in your dining room to correct improper placement of the salad forks.

I really suspect a bug in the application.

---

### Post by Boab1993 on 2013-08-16
> **P3n6uin said:**
> I'm not sure what website you're referring to but as for nuke, I'm referring to wiping the hd.
If the data is corrupt this ought to resolve the issue.
Thanks again.

Apologies, i was thinking you were trying to connect to externally hosted drive, that you didnt have authority on.

But thanks for the info on nuking.

---

### Post by P3n6uin on 2013-08-17
> **QIII said:**
> But why on earth would you want to nuke an entire drive to correct a problem with the data for one application?

That's like throwing a hand grenade in your dining room to correct improper placement of the salad forks.

I really suspect a bug in the application.

I'm not sure your metaphor is all that accurate. If the salad forks were in some way unusable I wouldn't throw a hand grenade, I'd simply get other functional forks.

Wouldn't a bug in the app give the same results with the other player?

---

### Post by P3n6uin on 2013-08-17
> Apologies, i was thinking you were trying to connect to externally hosted drive, that you didnt have authority on.

I see.
Your reply really had me scratching my head.

---

