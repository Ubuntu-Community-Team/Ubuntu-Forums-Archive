---
title: "How to copy Amarok statistics between different collections."
date: 2008-09-28
forum: Outdated Tutorials &amp; Tips
---

### Post by hazica on 2008-09-28
Having problems with your Amarok 1.4.x MySQL collection but are reluctant to start from scratch because you have years worth of ratings, scores and playcounts stored in it? Want the statistics of your desktop collection on your laptop? Then give this solution a try. (I offer absolutely no guarantee that it will work and I take no responsibility for any harm done to your collection; all I can say is that it worked for me twice and as long as you back up your data as described, it should be perfectly safe)

This guide assumes that you already have Amarok configured for MySQL and that your collection has been scanned and stored in MySQL. (As described here: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo) ) It will only work for files which are identical copies of each other (that share the same *uniqueid*). This means that if you have a file *[john_coltrane-blue_train.mp3* on your desktop and *john_coltrane-blue_train.mp3* on your laptop, but have altered the tags of one of the files after having copied them, the statistics for that song won't be transferred from one collection to the other.

You basically have two databases: your current - *target* - Amarok database (which doesn't have to contain any statistics) and your *source* database - the database you want to copy the ratings from.

Create dumps of both databases: *source.dump* (which will provide the ratings) and *target.dump* (which constitutes a backup, so that in case anything goes wrong, you'll be able to revert to your initial collection/stats)

To create a dump, issue the following command:
	
	```
mysqldump -p -u root DATABASE_NAME > filename.dump
```


For instance, if I want to get the ratings from my desktop collection onto my laptop, I'd dump my desktop collection into *source.dump* and I'd make a safety backup *target.dump* of my laptop collection.

The following operations will be performed on the _target machine only_.

So, here we go:

Create a new database called source on the target machine 

	```
$ mysql -p -u root
CREATE DATABASE source;
GRANT ALL ON source.* TO amarok@localhost IDENTIFIED BY 'amarok';
FLUSH PRIVILEGES;
QUIT;
```

and import the *source.dump* in the source table like so:

       ```
$ mysql -p -u amarok -h localhost source < source.dump
```

Now, in order to simplify the way we interact with the databases, copy the table ***source.statistics*** into the ***amarok database*** under a different name - "***statistics_source***" for instance . In order to do this, we first have to create the new table in the ***amarok*** database:
	
	```
$ mysql -p -u amarok
CREATE TABLE amarok.statistics_source LIKE amarok.statistics;
```

Then we copy the information from ***source.statistics*** into the newly created ***amarok.statistics_source*** like so:

	```
INSERT amarok.statistics_source SELECT * FROM source.statistics;
```

Now we have both statistics tables in the ***amarok*** database; the source database can therefore be deleted:
	
	```
DROP DATABASE source;
```

And now, for the interesting part. We create another intermediary statistics table in the ***amarok*** database, where we will store the ratings shared between the two collections.
	
	```
CREATE TABLE amarok.intermed_statistics LIKE amarok.statistics;
```

There are now three statistics tables in the amarok database:
	
[LIST]
[*]the original: statistics
[*]the source: statistics_source
[*]the intermediary: intermed_statistics
[/LIST]
The next step is the crucial one, where we extract the common elements from the ***statistics_source*** that already exist in the target database (based on their *uniqueid*) and insert them into the ***intermed_statistics*** table:

	```
USE amarok;
INSERT INTO intermed_statistics (url, deviceid, createdate, accessdate, percentage, rating, playcounter, uniqueid, deleted) SELECT uniqueid.url, uniqueid.deviceid, statistics_source.createdate, statistics_source.accessdate, statistics_source.percentage, statistics_source.rating, statistics_source.playcounter, uniqueid.uniqueid, statistics_source.deleted FROM statistics_source INNER JOIN uniqueid ON statistics_source.uniqueid = uniqueid.uniqueid;
```

Now we can drop the original ***statistics*** table and replace it with the new one:

	```
DROP TABLE amarok.statistics;
CREATE TABLE amarok.statistics LIKE amarok.intermed_statistics;
INSERT amarok.statistics SELECT * FROM amarok.intermed_statistics;
```

Start Amarok and check out the results!
If everything went smoothly, clean up your db:

	```
DROP TABLE amarok.intermed_statistics;
DROP TABLE amarok.statistics_source;
exit;
```

And you're done.

Hope you found this helpful.


EDIT: some time after I imported my ratings, I discovered that some titles had double entries. The way to fix this is to rescan the collection.

---

