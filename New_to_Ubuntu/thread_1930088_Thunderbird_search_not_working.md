---
title: "Thunderbird search not working"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by iangarforth on 2012-02-23
Hi all,

Whenever I search for something in Thunderbird, it now always returns zero results, no matter what I search for.

It used to work fine; trouble is, I can't remember whether this problem started when I moved to Thunderbird 10 recently.  Is there anything anyone can suggest?

Am on 11.10, FWIW.

Cheers

---

### Post by jtarin on 2012-02-23
Try opening your Home/Thunderbird/Profiles/(random).default folder and backup then delete the file global-messages-db.sqlite, and then restart Thunderbird. Wait a few minutes for the indexing to complete. Then try search.

---

### Post by iangarforth on 2012-02-23
I've renamed the file, and then restarted Ubuntu.  Thunderbird creates a new file, but doesn't seem to do anything to suggest it's re-indexing anything.

Is there anything else I can try?

---

### Post by jtarin on 2012-02-23
1. Quit Thunderbird
2. Locate your global-messages-db.sqlite file. Mine is in:
Home/Thunderbird/Profiles/cblcq8lr.default
3. Rename (or delete)**_ both_** **global-messages-db.sqlite** and **global-messages-db.sqlite.journal**
4. Restart Thunderbird
5. Reindexing begins (may take sometime dependent on the amount of mail you have.)

---

### Post by iangarforth on 2012-02-23
Thanks for not giving up, jtarin!

Ok - I have a global-messages-db.sqlite file, but not a global-messages-db.sqlite.journal

At least - I've searched within the Thunderbird folder, and it picks up the first, but not the second..?

---

### Post by jtarin on 2012-02-23
Try using [Thunderbird Conversations ]("https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view/"). When you first install Thunderbird Conversations it re-indexes your messages. It also provides a way to repeat this on demand.

Tools -> Add-Ons -> Extensions -> Thunderbird Conversations -> Preferences -> Start the setup assistant -> Apply changes

If you click Review changes before clicking Apply changes, you'll see that the following are checked:

    Make sure Global Search and Indexer is enabled.
    Re-index messages containing attachments as well as all Mozilla bugmail.

After doing so you can monitor progress with Tools -> Activity Manager

---

### Post by iangarforth on 2012-02-24
Still no dice :-(  I actually really like conversations view, but it shows no evidence of any indexing, no matter how many times I tell it to do it.  Still no search results no matter what I search for...

---

### Post by Elvis99 on 2012-05-31
> **iangarforth said:**
> Still no dice :-(  I actually really like conversations view, but it shows no evidence of any indexing, no matter how many times I tell it to do it.  Still no search results no matter what I search for...

I had the same issue, after deleting "global-messages-db.sqlite" and "global-messages-db.sqlite.journal" and restarting thunderbird the search still did not run. What I did was 
right-clicking on the inbox, select "compact" let it run throu and afterwards it should work.

---

