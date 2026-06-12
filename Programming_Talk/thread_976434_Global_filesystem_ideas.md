---
title: "Global filesystem ideas"
date: 2008-11-09
forum: Programming Talk
---

### Post by CrazyGuy123 on 2008-11-09
Hi,

I've been thinking of ideas for a single global distributed filesystem, and thought I'd mention them here so others can contribute.  The project status at the moment is design stage only, and development might happen if I get a lot of positive feedback and motivation.

[SIZE="3"]Problems[/SIZE]
Current filesystems run on one or a few disks, and if a few disks fail, all the data can be lost.  Current backup systems require a lot of storage space, and many users don't use backups at all, or not for all files.

In a global sense, a lot of files are stored in more than one place - eg. all the ubuntu operating system files are stored on millions of computers across the world, which is a lot of redundancy, possibly a lot more than is required, whereas other files, such as my holiday photos are stored on only my computer, which is a single point of failure - not good.

[SIZE="3"]Aims[/SIZE]
[LIST=1]
[*]**Store files redundantly across the globe**.  Any file should be stored in more than one place.
[*]**Reduce redundancy where unnecessary**.  Make sure no file is unnecessaraly stored in too many places - this just wastes space.
[*]**Provide fast access to files**.  Files should preferentially be stored in the locations they are frequently accessed,  even if this breaks the rule above.  This should allow me to use this global filesystem as a root filesystem for storing applications etc. on, since in most cases the file I'm accessing will already be on my local PC.
[*]**Store files near where they are used**.  If it's not possible to store a file locally, due to disk space limitations, it should be stored as near as possible to locally - so it should be stored on a Local LAN PC for example.
[*]**Provide failover**.  Since PC's in the global filesystem will be going online and offline frequently, when any system goes offline, the data it contained should be duplicated again elsewhere on the network, so that it isn't lost.
[*]**Provide Privacy**.  It shouldn't be possible for any peer on the network to see any other peers data - this is the hardest bit in the design - see below.
[*]**Provide protection against "bad" peers**.  Since there is just one global filesystem, it should be protected against users that abuse it.  Therefore we need to implement:[LIST]
[*]Bandwidth controls - a tit-for-tat system similar to peer to peer filesharing networks.  This won't be such a problem as in filesharing networks since users will WANT to upload data that they want stored.
[*]Space controls - make sure no user stores way more data on the network than they have space to give to other users of the network, taking into account the desired redundancy.
[/LIST]
[/LIST]

[SIZE="3"]Research[/SIZE]
Looking at my Ubuntu partition, here is a breakdown of the files I store, which is probably pretty close to a typical user:
Programs/Games/application binaries and data:  5GB
Text Documents/Work: 1GB
Videos/Music/Downloads:  10GB
Photos: 2GB
Free space:  2Gb

Of this lot, all except the documents and photos are likley to be on at least someone elses computer across the world.  That means, of the 18Gb of data I have, only 3Gb is unique to me.  The 3Gb of data could be redundantly stored in 3 places (totaling 9GB).  That means with the global filesystem, my HD usage could be:

3GB:  my personal data
6GB:  redundant copies of other peoples personal data
9GB:  a cache of the most frequently used operating system/application/data files that aren't unique to me.

[SIZE="3"]Privacy[/SIZE]
This is the hardest topic.  Here are my requirements:

No user may see another users data
Files that are identical on different systems must be identifiable so redundancy can be reduced/increased as necessary.

To achieve this, I propose the following encryption system:

[LIST=1]
[*]Take the original data in blocks and hash it.  This is hash 1 - the private hash.
[*]Use the hash as the encryption key to encrypt the data with a symmectric encryption algorithm
[*]hash the encrypted data.  This is hash 2 - the public hash.
[/LIST]

Hash 1 must be kept secret, and will be kept on the computer whose data it is.  If someone doesn't know hash 1 then even if they have the encrypted data, they can't decrypt it.

Hash 2 is the public hash used for identifying data.  If two systems have the same hash 2 then the data is the same.  Hash 2 can be used in a distributed hash table, like peer to peer networks for locating a particular piece of data around the globe.

This way, when a bit of data is encrypted it can be distributed around the globe without privacy risks.   The only problem with this scheme is a known-plaintext attack - ie. if an "attacker" knows the entire unencrypted contents of a file on your computer, they can be sure you own that file by requesting it from you.  This attack is thwarted by distributing the file pieces redundantly - then the attacker doesn't know if it's your file data or someone else's.

For any given file/block, both hashes must be stored to recover the data - one to find and download the data, and another to decrypt it.  These two would be stored in a directory index like a traditional filesystem.  Unlike a traditional filesystem, the directory index itself will be stored just like a file in the global filesystem.  This way if your hard disk dies, you only need to recover the root directory index, and that will give you hashes to recover every subdirectory.  This helps in data recovery - if your disk dies you only need to know two hashes to recover all the directories, and therefore all the files and their data from other peers on the network.

[SIZE="3"]Global Distribution[/SIZE]
Since after encryption file data and metadata are just bits of data, and the privacy issues have been removed, they can be distributed anywhere, and when they need to be referenced they will be found by hash (hash 2) only.  This means file data blocks can be sent to any PC who will treat them as his own blocks - ie. now the owner of the block is irrelevant.  All PC's will store a cache of their own blocks and others blocks, and not know the owner.

The following algorithm could be used to distribute the blocks:
each PC goes through every block in it's cache, and reports it to a "management" node, which is selected at random from the peers.

The management node keeps lists of which blocks each peer has, and checks with other management nodes to see which blocks are rarest.  Each block is given a rareness score.  If a block is too rare, it will be duplicated.  This score will also represent the load on the systems holding the block - if most of the systems holding a block are near or at their bandwidth limits, the block will be duplicated to reduce load.

[SIZE="3"]Block combining[/SIZE]
Many blocks will only have one owner, and if that owner uses the file they will be cached local to that owner, and therefore infrequently accessed on the network - In fact the only time they will be accessed is during data recovery in case the cached copy is lost. In this case, the only requirement is that the blocks are always accessible, while using as little global storage space as possible.  To achieve this I propose the following "block splitting" algorithm.

Take the original data, possibly in huge "superblocks".

Split the data into say 10 parts.  Create a further 5 "recovery parts" using error correction codes.  From these 15 parts, if any 10 are available, the original data can be recovered.  This data can now be distributed round the network, and each part is only stored in one place (no redundancy).  The supernodes will make sure that at all times all 15 parts are available.  If one or more parts goes offline then 10 of the other 14 parts will be used to regenerate more recovery parts.  This way the total storage space used by the file on the network is 1.5x the size of the file, and the data is only lost if 5 peers all go off-line simultaneously.

Also, when recovering the file data, any 10 of the 15 peers can be contacted to recover the data block - this allows good load balancing since heavily loaded peers don't need to be used.

[SIZE="3"]Positive Side Effects[/SIZE]
[LIST=1]
[*]**"Instant" downloads** - If a publisher published the hash of a file or folder, a user could add that file or folder to his own filesystem.  The file will later be cached transparently on his/her system, but can be accessed immediately.  Effectively, that means a video/audio file could be "streamed" across the network, downloading and playing as the application accesses it.
[*]**"Instant" program/operating system installation** - an entire program or operating system could be installed just by simply adding the hashes for it's files and folders from the software vendor, and then running any system-specific configuration scripts.  Again the actual data transfer happens in the background out of sight and transparently.  For example while ubuntu is 700MB on a CD, only about 100MB of data is required to boot it up, so you could start using it when just the first 100MB was done.
[*]**Backups at every point in time** - just by accessing last weeks root directory hash, you can see what all your data looked like last week.
[/LIST]

*(this is all for now - I'll add more details later.  In the meantime, feel free to add suggestions)*

---

### Post by Ferrat on 2008-11-09
in theory this would be great but then you got problems as 

Security - no matter what you do someone will crack it in a day or less

Intellectual Property and Copyright - not only the security but you don't have the right to spread some things even if encrypted.. 

Privacy - I understand the backup but say your computer crashes, that means you have to have a personal signature to find your data, that means someone could find your signature and locate all your data? 

Also say I throw away my computer, but copy all my files that I want, connect that either I have to sync with all the other backups or just create a new one = more useless space taken. 
Register 5000 accounts and flood everyone with useless backup-data and cripple their connection??

Problems with connection = no OS or a gimped on?

Also would require people to hand over control of their system to your network, say someone needs that extra GB and someone else's data is there, does he have the right to delete it? 

How often will it update? since the more = more safety but also takes more band, also some connections might not be able to handle the load, some connections are limited amount of data etc.?

I'm not out to be mean but you've just skimmed the surface of all the problems that would occur and that's mostly technical, geting in to the legal stuff etc since for ex. any data traffic going in to or out of France has to be decoded and open but some docs etc might not be allowed to be that way? 
Some research encrypted or not may not be sent to some countries from for ex. USA, so you have to make an option to block those paths and computers, also you can't really count on the user knowing every country's rules so that means you have to and adapt a system that doesn't break them etc.

---

### Post by CrazyGuy123 on 2008-11-09
Ferrat:
You raise some good points.

deleting someone elses stuff wouldn't be a problem - it would be handled just as if the data had gone offline or been corrupted/lost - ie. the data duplication algorithm would recover the data from another copy and store it on another system elsewhere on the network.

As far as "clogging" the network with data, a simplistic solution would be to say the amount of data any user could have on the network shall always be no greater than the amount of storage space provided by their system.  This is easy with centralized management, but more of a challenge with a fully decentralized system.  Obviously due to duplication it would actually probably be possible for every user to store far more data on the network than they provide to the network due to the fact some data blocks are common between users, but the more data a user stores, the less room they have for a cache of their own data, so the slower access to their own files becomes.

The security of the system is really 2 parts:

[LIST=1]
[*]**Security (privacy) of user data** :- this is relatively easy to achieve provided you can find a secure symmetric encryption algorithm, of which there are a few around (eg. Blowfish)
[*]**Security of the network against abuse** :-  this is harder as there are so many possible attacks - in general abuse of the network is hard to control with an entirely decentralized system (since any number of peers could be "bad", and you can't trust any other peer).  For that reason I'm considering implementing it initially as a system with a central block management server, as well as a de-centralised model to move to if it becomes widely used (since then a central server will be loaded too much, and is an unacceptable reliability problem).  I suspect this will be the biggest problem to overcome.

Having said that, there will be no motivation for a user to abuse the network, since they can never get access to someone else's data, and can't attack any individual personally, so abuse of the network could be considered similar to blocking up a network by flooding it with packets
[/LIST]

Legal problems.  From a legal standpoint, this is the same as using an online backup tool for encrypted data or transferring data over the internet with a VPN.  Eventually it will be up to users if they can use it.  I know for sure that military grade secret data can pass over public networks as long as it's encrypted with a certified algorithm, so I can't see it as being a big problem, and if it is I propose those users just don't use this filesystem.

"Signatures".  Yes the "signature" to get all your data is the two hashes of the root directory you want to access.  If anyone gets hold of these they can access all your data (although they can't modify it).  These keys need to be kept as secure as say your pgp keys.  For "low" security they could be stored on your system and secured by the kernel so no malware could access it unless it was running as root.  For high security they could be encrypted with a master password like full disk encryption schemes.  The signatures would be short enough you could print them off on paper and keep them under your bed if you wanted! :-).  One issue with signatures at the moment is with the current scheme the signature of a folder changes if any file within that folder or any sub-folders change, but I'm sure that can be worked round.

One really good thing about these signatures is if you wanted to intentionally share them it's equivilant to sharing the whole folder structure - so for example I could email you the signature of one folder on my computer, and that would automatically give you access to the entire contents of the folder from the global network, which would self-replicate to cache the data on your PC a well when you access it.


Load - You mention bandwidth use/caps etc.  The software could be configured to limit bandwidth or data transfer per day.  This wouldn't be detrimental to the network, because if you have a low speed connection that just means the network will organise itself to have rarely accessed data saved on your PC, and more frequently accessed data elsewhere on the network.  The diadvantage for you would be that access to your own data would also be slowed by the same factor. 

I don't believe data transfer limits will be a problem - if the average user has 250GB of data on the network, of which 20GB is unique to them, and 500MB of that changes per week, provided new data on your PC was only given redundancy on the network once a week and with a 1.5x redundancy, that would only be 750MB up and 750MB down on average per user per week.  

What will be more of a problem is connection speeds and latency.  When you want access to a file that you own, but has been lost or isn't in your cache, then you will need to get it from the network.  Since apps are designed to run from HD's with latency measured in ms, when it needs to do multiple network requests to find a few kb of data which end up taking several seconds it could make a program sluggish.  To get around that local data block caches will need to be big - probably 10's of GB for the average user.


As far as offline handling is concerned this is hard - the user will still have access to the OS, since it will be in the cache, together with most recently used data and files.  The problem happens when the user tries to access some program or file that isn't in the cache because it hasn't been used for many months.  This wouldn't be a problem except handling of this situation when it arises is hard - in most cases the program or even operating system would crash, since it can't access a file.  One option for solving this would be an option to "pin" certain folders in the cache, so they were always available and never flushed out.

---

### Post by achelis on 2008-11-09
PAST is i Peer-to-peer storage facility (not sure it was ever used). Maybe looking into the details of that will give you some ideas - and maybe you've already been there, done that :)

Good luck either way.

---

