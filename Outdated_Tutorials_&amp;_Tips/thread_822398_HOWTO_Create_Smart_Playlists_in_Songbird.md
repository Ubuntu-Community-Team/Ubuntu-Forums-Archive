---
title: "HOWTO: Create Smart Playlists in Songbird"
date: 2008-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by dwally89 on 2008-06-08
Songbird doesn't have the feature for Smart Playlists built into it (playlists that consist of music matching certain conditions, e.g. "Never been played", or "Recently Added").

So far I've only been able to make a Recently Added playlist, but if other people know how to make other playlists, then feel free to tell me and I'll add it to this post.



How to make a Recently Added playlist:
1. Open Text Editor (Applications>Accessories>Text Editor)
2. Copy and paste: 
```
find "/home/user/Music/" -mtime -30 -type f | egrep -vi '\.jpg$' >recentlyadded.pl
```
Change /home/user/Music/ to the directory where you store your music.
By default I've defined "recently added" as music that was added in the past 30 days, but you can change the number 30 to a different number if you prefer.
3. Click File>Save As... and call it RecentlyAddedPlaylist.sh (or something else if you prefer).
4. Navigate to the folder where you saved it, right click on it, click Properties.
5. Go to the Permissions tab and tick the box "Allow executing file as program" and click Close.
6. Double click on the file and click Run in Terminal
7. Open Songbird
8. Click on File>Import a Playlist...
9. Navigate to your home folder.
10. The playlist won't be visible, so just type "recentlyadded.pl" and click Open.
11. You should now see a playlist of all the songs you've added in the past 30 days.

To update the playlist, simply run steps 6 to 10 again.

EDIT: Songbird now contains a Smart Playlists feature (as of 0.7.0), but this tutorial might still be helpful for people wanting to create scripts

---

