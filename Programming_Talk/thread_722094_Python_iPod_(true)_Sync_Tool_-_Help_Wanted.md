---
title: "Python iPod (true) Sync Tool - Help Wanted"
date: 2008-03-12
forum: Programming Talk
---

### Post by booljayj on 2008-03-12
I have an idea for a tool that will allow a true iTunes-like sychronization of an iPod. This synchronization needs to be able to do the following things (more features could be added, but these are the absolute essentials):

- Use the native Rhythmbox database as a local music database
- Compare the iPod database and the Rhythmbox database to find duplicates so that only new songs are synchronized
- One- or Two-way sync configurable
- Configurable to sync whole library or just certain playlists
- On-the-fly encoding of songs as they are transferred using a set of user-defined "rules" (see below)
- Small and simple, following unix philosophy.

I think that for now, python is the best language to program this in. C++ would be a better alternative, but I don't know how to write it.

What I am really looking for here is suggestions or people who want to contribute to this project. I am not much of a programmer -- I usually just cut and paste code together from things other people made -- but I am a great project manager.

Let me explain some specifics about my reasoning behind this project. I think that this program should use the Rhythmbox database, but it most certainly MUST be separate from the rhythmbox application. It cannot be a plugin. We should use the rhythmbox database because it is a representation of the music the user already has and listens to, and making another identical database for an iPod transfer wastes space. It also allows the user to use their media player to manage their iPod transfers rather than the transfer program itself. It should not be a rhythmbox plugin because it needs to be able to run when rhythmbox is not running and also should support other media player databases in the future.

The encoding "rules" system is something that I came up with after the frustration of trying to convert my high-quality ogg and high-quality mp3 collection to lower-quality mp3 suitable for an iPod. The user defines a set of commands, if-then statements, that the program will use when converting the song files. This system should work like this:
If { ogg } at bitrate { any }
   then convert to { mp3 } at bitrate { 160 } with { vbr }
If { mp3 } at birtate { >=192 }
   then convert to { mp3 } at bitrate { 160 } with { vbr }
The above rules say that any ogg file should be converted to a 160 kb/s VBR mp3, and any mp3 above or at 192 kb/s should be converted to a 160 kb/s VBR mp3. This is useful not only for converting incompatable formats, but for shrinking the music files in order to get the most out of an iPod without shrinking the original file. I DON'T want to convert my 320 kb/s mp3s to a lower bitrate, but I also don't want them to take up 10 mb when they only need to take up 2 mb. Get my drift? The user can define any rules they want, or just ignore it altogether if they don't need it. Either way, everybody's happy.

Mplayer should be the main choice for conversion. It supports everything and doesn't require the use of separate encoders/decoders. Plus, a majority of Ubuntu users have it installed, so it wins the default vote. That's another key aspect of this project: it should only use widely-used libraries so that installation of extra libraries is kept to a minimum.

So what do you say, anyone want to help give Apple a good punch in the face and make Ubuntu the mainstream media choice of the masses?

---

