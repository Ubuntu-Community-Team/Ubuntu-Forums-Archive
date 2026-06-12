---
title: "Any way to stop curses from crashing on resize?"
date: 2009-08-22
forum: Programming Talk
---

### Post by pepperphd on 2009-08-22
Hi. I've been using the curses library with python for a few projects.  It is a little frustrating that something as simple as resizing the terminal can easily crash curses, and google is failing me for answers.  If anyone here has good experience with curses, how do you prevent silly crashes like this?

---

### Post by johnl on 2009-08-22
Hi,

When the terminal window size changes your application should receive a SIGWINCH signal.  You should catch this signal and perform any resizing logic when you receive it.

[this site](http://invisible-island.net/ncurses/ncurses.faq.html#handle_resize) has a pair of suggestions on how to respond to this signal.

Hope this helps.

---

### Post by geirha on 2009-08-22
Would be very helpful if you provided some code that has this problem. Preferably as small as possible.

---

### Post by pepperphd on 2009-08-22
> **geirha said:**
> Would be very helpful if you provided some code that has this problem. Preferably as small as possible.

Okay. Here are 3 functions that I use to put information on the screen. Resizing the playlist window causes curses to crash.

[php]
def make_playlist_window():
254 
255     """
256         i believe this speaks for itself, but pylint complains about 
257         even the simplest undocumented function ;)
258     """
259 
260     SPACE_FOR_FILLER = 5
261     begin_x = 5
262     begin_y = 2
263     height = len(displayed_songs) + 2
264     width = find_longest_song() + SPACE_FOR_FILLER
265     playlist_window = curses.newwin(height, width, begin_y, begin_x)
266     playlist_window.box()
267     return playlist_window

[/php][php]
def make_display_list(cursor, current_song):
210 
211     """
212         attempts to create a list of songs for the playlist window
213         based on the cursor position and/or the song being played
214         for small playlists (index error) it just returns the playlist
215     """
216 
217     displayed_songs = []
218     begin = -9
219     end = 11
220     if cursor != current_song:
221         center = cursor
222     else:
223         center = current_song
224     if len(playlist) -1 < -begin + end:
225         end = len(playlist) -1 + begin
226     i = begin
227     try:
228         while i < end:
229             if i + center > len(playlist) -1:
230                 for x in range(end - i):
231                     displayed_songs.append(playlist[x])
232                 return displayed_songs
233             displayed_songs.append(playlist[center + i])
234             i += 1
235         return displayed_songs
236     except IndexError:
237         return playlist

[/php]


Here, the songs that make_display_list determines will be shown are put on the screen.  Resizing the terminal window to a size smaller than needed to complete this function throws an error.
[php]
def show_playlist(cursor, current_song):
271 
272     """
273         here the songs obtained from make_display_list() are shown
274         in one of three ways. the current song is always highlighted in white.
275         the song the cursor is over, if it isnt the current song, is highlighted
276         in red. and all other songs are simple white on black
277     """
278 
279     displayed_songs = make_display_list(cursor, current_song)
280     i = 0
281     for song in displayed_songs:
282         if song == playlist[current_song]:
283             playlist_window.addstr(i + 1, 2, song[song.rfind("/") + 1:], curses.color_pair(1))
284         elif cursor != current_song and song == playlist[cursor]:
285             playlist_window.addstr(i + 1, 2, song[song.rfind("/") + 1:], curses.color_pair(2))
286         else:
287             playlist_window.addstr(i + 1, 2, song[song.rfind("/") + 1:])
288         i += 1
[/php]

---

