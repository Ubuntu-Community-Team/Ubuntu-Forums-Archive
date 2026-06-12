---
title: "[SOLVED] rhythmbox"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by DarinB on 2008-11-10
I will try to post this here!
i did a clean install of intrepid.
when i click update for podcasts frequently it closes.
then i have to reopen it. sometimes several times in a row.
Any Ideas???????

---

### Post by PmDematagoda on 2008-11-10
By closes, do you mean it crashes?

If it crashes, then start Rhythmbox through the terminal and post the output on the terminal here after it crashes.

---

### Post by DarinB on 2008-11-10
stupid question how do i do that Open through terminal? and that is after it shuts down?

---

### Post by Ryadt on 2008-11-10
It means, start it from the terminal by typing the rhythmbox code.

---

### Post by DarinB on 2008-11-10
of course! i am trying to get rhythmbox to crash and it wont no matter what i do.
it will happen when i least expect it. like going to the garage and the noise stops.

---

### Post by DarinB on 2008-11-10
here is the terminal info after crash

darin@darin-desktop:~$ rhythmbox

(rhythmbox:11824): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

---

### Post by redseventyseven on 2008-11-10
That's a warning about one of your icons in your icon theme which rhythmbox wants to use being not properly configured, but that probably isn't the cause of your problem.

Was there anything else in the terminal window? Any other messages? Also, after it "crashed", did you get your command prompt again? If not, then the program is probably still running somewhere but has just disappeared, rather than crashed completely and quit unexpectedly.

---

### Post by DarinB on 2008-11-10
i think it is quiting unexpectedly, how do I fix it????

---

### Post by DarinB on 2008-11-12
i got a terminal response for the rhythmbox shut downs that occur regularly now  check the last entry i have no idea what it means but someone will????? 
darin@darin-desktop:~$ rhythmbox

(rhythmbox:7925): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

/usr/share/apport/apport-gtk:189: GtkWarning: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

  self.w('window_information_collection').show()

(firefox:8124): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field


(firefox:8143): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field


(rhythmbox:7925): Rhythmbox-WARNING **: Unhandled error: Unknown playback error
**
RhythmDB:ERROR:rhythmdb-tree.c:1637:rhythmdb_tree_entry_delete: assertion failed: (g_hash_table_remove (db->priv->entries, entry->location))
Aborted
darin@darin-desktop:~$

---

### Post by PmDematagoda on 2008-11-12
Does this happen with a specific song or set of songs or is it just totally random?

---

### Post by DarinB on 2008-11-13
some times when i click a radio station or podcast or simply delete an old podcast by right click delete.

---

### Post by DarkN00b on 2008-11-14
I have a similar problem in that Rhythmbox closes every time it completes a download, regardless of the source.

---

### Post by rotwang888 on 2008-11-14
I'm having a similar problem with rhythmbox vanishing and acting strangely with podcasts.  I think I'm just going to move my feeds to something else but I'd love to know what the problem ends up being.  You might want to look in system monitor and see if process "gvfsd-http" is using a lot of memory.  It was for me, because podcasts were staying in memory even after I'd deleted them in rhythmbox.

---

### Post by DarkN00b on 2008-11-14
> **rotwang888 said:**
> I'm having a similar problem with rhythmbox vanishing and acting strangely with podcasts.  I think I'm just going to move my feeds to something else but I'd love to know what the problem ends up being.  You might want to look in system monitor and see if process "gvfsd-http" is using a lot of memory.  It was for me, because podcasts were staying in memory even after I'd deleted them in rhythmbox.

Wow, you're right. gvfsd-http is currently using 625MB of my ram. Here's the error I'm getting in my syslog:

```
Nov 14 00:46:26 darkn00b-desktop kernel: [58112.189719] rhythmbox[13734]: segfault at 632f6d6f ip b71865c8 sp b4a95260 error 4 in libgobject-2.0.so.0.1800.2[b715d000+3c000]
```

Does anyone know an easy way to import my podcast settings into Banshee? :D

---

### Post by DarinB on 2008-11-14
this memory thing sounds like a good possibility mine shuts down when i am deleting old podcasts or changing radio stations,,,how do i monitor the crashes or set up sys log??????

---

### Post by fondfire on 2008-11-15
Hi, I've also been having a lot of serious problems with Rhythmbox.  I think it's certainly related to Podcasts, of which I currently stream 54.  In case it matters, I'll also mention that I use Xubuntu and an Xfce desktop.  This may be more of a problem with Rhythmbox in Xfce than Rhythmbox in general, but I have my doubts.

I noticed the problem seems to occur when I am already playing an already downloaded podcast and a new episode of any of the 54 streams finishes downloading in the background (and though it *may* only be when certain podcasts download and not others, I haven't determined that).  Sometimes it simply seems to happen when I get a lot of podcasts downloading at once.

I'm also noticing the massive related problem with the memory leak of the gvfsd-http process.  I keep reading in various posts on various forums on the web that this is due to it retaining downloads in memory after they're downloaded.  That strikes me as a particularly bad design idea, given the amount of podcasts I get from the web.  Shortly after updrading to Intrepid, I had a few fabulous total system lock-ups requiring power-button resets, due to gvfsd-httpd filling-up my memory and swap space and freezing everything up totally.  To me, having to go kill gvfsd-http by hand periodically has seriously dampened my up-to-now quite enjoyable Xubuntu experience (which has been going on for almost two years).  However, killing gvfsd-http doesn't seem to cause any serious problems.  The process just gets restarted the next time something is about to get downloaded.  (On a related note, I think Firefox may also lean on gvfsd-http for at least certain types of downloads, but I'm not absolutely sure about that.  Since gvfsd-http is a generic utility, I'd this this aspect affects more apps than Rhythmbox, unless Rhythmbox isn't sending some kind of "download complete, so free that memory" message back to gvfsd-http.)

I am having some troubles with two feeds.  One of them fails utterly (and it didn't before the upgrade to Intrepid) and this is the output on that from running 'rhythmbox -d' at the command line and then attempting to refresh that particular podcast:

    (14:24:01) [0x20ac500] [rb_podcast_source_cmd_update_feed] rb-podcast-source.c:1553: Update action
    (14:24:01) [0x305df00] [rb_podcast_manager_thread_parse_feed] rb-podcast-manager.c:1043: attempting to parse feed [http://speakingoffaith.org/podcast/podcast.xml](http://speakingoffaith.org/podcast/podcast.xml)
    (14:24:01) [0x305df00] [rb_uri_could_be_podcast] rb-file-helpers.c:376: 'http://speakingoffaith.org/podcast/podcast.xml' should be Podcast file
    (14:24:01) [0x305df00] [rb_podcast_parse_load_feed] rb-podcast-parse.c:155: not checking mime type for [http://speakingoffaith.org/podcast/podcast.xml](http://speakingoffaith.org/podcast/podcast.xml) (should be Podcast file)
    (14:24:02) [0x305df00] [rb_podcast_parse_load_feed] rb-podcast-parse.c:206: Parsing [http://speakingoffaith.org/podcast/podcast.xml](http://speakingoffaith.org/podcast/podcast.xml) as a Podcast failed

I wish I could provide something more definite, like what exactly about the parsing failed (as I eyeballed the page source and nothing seemed wrong with the formatting, though that doesn't mean much).

Also, the MP3's downloaded from this feed, <http://www.townhall.com/talkradio/podcast.aspx?RadioShowId=60>, will not play properly in Rhythmbox, though they do play properly in Audacious.  If it plays properly in Audacious, can Rhythmbox be made to do it, too?

Perhaps this e-mail was better suited to be posted on the Rhythmbox forums, but I saw this thread here and thought I'd share my experience.  Any fixes would be appreciated.

--Fondfire

---

### Post by DarinB on 2008-11-15
now that i am not alone in this rhythmbox dilemma what do we do about it???????????????????????????????????????????????????
i use gnome and don't suggest amarok!!!!! no matter what people say amarok is even buggier with gnome that rhythmbox is, on a bad day......
The truth is!!!when i get the suggestion to use something else that is a cheap suggestion....i have been using rhythmbox since 7.04 and only now with this new version in intrepid is a problem.

---

### Post by DarinB on 2008-11-15
about rhythmbox forums i am also trying that as well i have had some suggestions but none have come as close as this memory use problem.
i also have noticed that if i let the updates finish and don't click too fast it seems to stay open, not ideal i would like it to work as it used to under the last rhythmbox version in hardy.

---

### Post by rotwang888 on 2008-11-18
> **DarinB said:**
> now that i am not alone in this rhythmbox dilemma what do we do about it?????????????????????????????????????????????????
 No idea.  Maybe vote in [this thread](http://brainstorm.ubuntu.com/idea/15509/)?

---

### Post by fondfire on 2008-12-12
Well, I attempted to [post a message on the Rhythmbox developers forum]("http://mail.gnome.org/archives/rhythmbox-devel/2008-November/msg00047.html") and they don't appear to be very responsive.  I will leave a comment on [the referenced thread]("") and start assessing other players . . .  Rhythmbox has simply become unbearably buggy for heavy use, which I find unfortunate, as previous to 8.10 Intrepid Ibex's Rhythmbox 0.11.6, I was really pleased with it.  As no fixes have been released for this buggy version, I need to swap over to something that actually works.  ](*,)  I wish I knew how to look at the source and actually help, but unfortunately, all I can do is eyeball config files and test the app.

Alert me if anything gets better.

--Fondfire

---

### Post by fondfire on 2008-12-12
I decided to try to submit [a bug]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/307365") before totally giving-up.  I hope I submitted it correctly . . .

--Fondfire

---

