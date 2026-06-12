---
title: "Cron won't run Python Twitter Bot"
date: 2015-02-08
forum: Programming Talk
---

### Post by dizzydez on 2015-02-08
It runs perfectly manually and in cron's bash environment - so I'm assuming there might be something about crontab in the OAuth process itself? I have tried running env in cron and pasting the PATH I found there also...

twitter_follow_bot.py
```

[FONT=Menlo][COLOR=#34bbc7]**from**[/COLOR] twitter [COLOR=#34bbc7]**import**[/COLOR] Twitter, OAuth, TwitterHTTPError[/FONT]
[COLOR=#34BBC7][FONT=Menlo]**import**[COLOR=#000000] os[/COLOR][/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[COLOR=#C33720][FONT=Menlo]**# put your tokens, keys, secrets, and Twitter handle in the following variables**[/FONT][/COLOR]
[COLOR=#34BD26][FONT=Menlo][COLOR=#000000]OAUTH_TOKEN = [/COLOR]**"..."**[/FONT][/COLOR]
[COLOR=#34BD26][FONT=Menlo][COLOR=#000000]OAUTH_SECRET = [/COLOR]**"..."**[/FONT][/COLOR]
[COLOR=#34BD26][FONT=Menlo][COLOR=#000000]CONSUMER_KEY = [/COLOR]**"..."**[/FONT][/COLOR]
[COLOR=#34BD26][FONT=Menlo][COLOR=#000000]CONSUMER_SECRET = [/COLOR]**"..."**[/FONT][/COLOR]
[FONT=Menlo]TWITTER_HANDLE = [COLOR=#34bd26]**"..."**[/COLOR][/FONT]
[FONT=Menlo]
[/FONT]
[COLOR=#C33720][FONT=Menlo]**# put the full path and file name of the file you want to store your "already followed"**[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo]**# list in**[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo]**# OMITTED - ALREADY_FOLLOWED_FILE = "already-followed.csv"**[/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]t = Twitter(auth=OAuth(OAUTH_TOKEN, OAUTH_SECRET,[/FONT]
[FONT=Menlo]            CONSUMER_KEY, CONSUMER_SECRET))[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo][COLOR=#34bbc7]**def**[/COLOR][COLOR=#5330e1]** search_tweets**[/COLOR](q, count=100, result_type=[COLOR=#34bd26]**"recent"**[/COLOR]):[/FONT]
[FONT=Menlo]    [COLOR=#34bd26]**"""**[/COLOR][/FONT]
[FONT=Menlo]        Returns a list of tweets matching a certain phrase (hashtag, word, etc.)[/FONT]
[FONT=Menlo]    [COLOR=#34bd26]**"""**[/COLOR][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    [COLOR=#34bbc7]**return**[/COLOR] t.search.tweets(q=q, result_type=result_type, count=count)
[/FONT]
```
startuprun.py
```

[FONT=Menlo][COLOR=#34bbc7]**from**[/COLOR] twitter_follow_bot [COLOR=#34bbc7]**import**[/COLOR] auto_fav[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]auto_fav([COLOR=#34bd26]**"startup"**[/COLOR], count=100)[/FONT]

```
sudo crontab -e (the last line is an alternate tester - today is "7" in cron's calendar..
```

[FONT=Menlo]PATH=/usr/bin:/bin[/FONT]
[FONT=Menlo]SHELL=/usr/bin/bash[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]*/15 * * * * 1-2 /usr/bin/python [/FONT][FONT=Menlo]/var/www/html/twitter/[/FONT][FONT=Menlo]startuprun.py  >> /tmp/cron.output[/FONT]
[FONT=Menlo]*/15 * * * 3-4 /usr/bin/python [/FONT][FONT=Menlo]/var/www/html/twitter/[/FONT][FONT=Menlo]entrepreneurrun.py  >> /tmp/cron.output[/FONT]
[FONT=Menlo]*/15 * * * 5-6 /usr/bin/python [/FONT][FONT=Menlo]/var/www/html/twitter/[/FONT][FONT=Menlo]venturecapitalrun.py  >> /tmp/cron.output[/FONT]
[FONT=Menlo]*/1 * * * 7 /usr/bin/python [/FONT][FONT=Menlo]/var/www/html/twitter/[/FONT][FONT=Menlo]techrun.py >> /tmp/cron.output[/FONT]
[FONT=Menlo]*/1 * * * 7 python [/FONT][FONT=Menlo]/var/www/html/twitter/[/FONT][FONT=Menlo]techrun.py >> /tmp/cron.output[/FONT]

```

Errors are no longer writing to cron.output so I think it might be on twitters end.

 Anyone know of any issues between cron and the authorisation process? Or maybe something else that I've missed? I've also tried putting a shebang for bash, python at the top of crontab but no joy...

---

