---
title: "xchat fun fake version request"
date: 2011-02-26
forum: Programming Talk
---

### Post by bashologist on 2011-02-26
Settings --> Advanced --> CTCP Replies --> Add New.
In first box put "VERSION" and in the second put "fakeversion %s".
The script has to be loaded, so save the script with a name like fakeversion.pl and then put it in $HOME/.xchat2/ so it's automatically loaded on xchat startup.
Stop xchat from sending the real ctcp version by entering this command in xchat.
```
/set irc_hide_version on
```
Test it out on yourself...
```
/ctcp yournickname version
```
Edit script to your liking.

```
use Xchat qw(:all);
register("Fake version reply", "1.0", "Fake version reply");
hook_command("fakeversion", \&fakeversion);

sub fakeversion {
	$nick = $_[1][1];
	$sent{$nick}++;
	if ($sent{$nick} lt 2) {
		command("nctcp $nick VERSION me again and I kill the bunny. I'm ******* serious.");
		command("nctcp $nick (\\(\\");
		command("nctcp $nick (^.^)");
		command("nctcp $nick (\")_(\")");
	} elsif ($sent{$nick} lt 3) {
		command("nctcp $nick (\\(\\        ...Cough...Cough...Cough...");
		command("nctcp $nick (x.x)    ...Why would you make him kill me.... ");
		command("nctcp $nick (\")_(\")     ...You're going to hell for this.....");
	} elsif ($sent{$nick} lt 4) {
		command("nctcp $nick VERSION me again and you'll end up like the bunny.");
	}
	return EAT_ALL;
}
```

This is what three ctcp version requests look like...
```
>bashologist< CTCP VERSION
* Received a CTCP VERSION from bashologist
-bashologist- VERSION me again and I kill the bunny. I'm ******* serious.
-bashologist- (\(\
-bashologist- (^.^)
-bashologist- (")_(")
>bashologist< CTCP VERSION
* Received a CTCP VERSION from bashologist
-bashologist- (\(\        ...Cough...Cough...Cough...
-bashologist- (x.x)    ...Why would you make him kill me.... 
-bashologist- (")_(")     ...You're going to hell for this.....
>bashologist< CTCP VERSION
* Received a CTCP VERSION from bashologist
-bashologist- VERSION me again and you'll end up like the bunny.
```
It seems the forum doesn't like my bad language and so replaced the word with asterisks lol. I shouldn't have used bad language anyways.

---

