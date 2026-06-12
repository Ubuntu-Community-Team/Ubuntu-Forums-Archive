---
title: "Commenting individual parts of code using doxygen"
date: 2009-10-08
forum: Programming Talk
---

### Post by alzaf on 2009-10-08
Is it possible to comment code inside python function body so that it is readable when viewing it yet can be picked up by doxygen?

To give an example, the following function is commented for doxygen.

```
#*******************************************************************************************************************
## @brief Get scores from ablum copied over and increase by one 
#  @param album_name Name of album
#  @param artist_name Name of artist
#  @param discnum Disc number of album
#
#  @details A query is sent to query_dbase function to get the score of album using passed parameters. The score
#  is extracted by passed query results then increased by 1. The album is updated with new score 

#*******************************************************************************************************************
def update_score_tags(album_name, artist_name, discnum):
		
	# Set sqlite query into dbq with passed parameters.
	dbq = 'select distinct score from tags where album = "%s" and artist = "%s" and discnum = "%s"' % (album_name, artist_name, str(discnum))
   
        # Pass query to query_dbase where results will be returned into
        # into old_album_score
	old_album_score = query_dbase(dbq)
		
	# Increase score by 1 and update database
	new_album_score =  old_album_score[0][0]
	new_album_score = new_album_score +1

        # Set query to set album score to new value and pass to exec_dbase
        # so sqlite database is updated.
	dbq = 'update tags set score = "%s" where album = "%s" and artist = "%s" and discnum = "%s"' % ( str(new_album_score), album_name, artist_name, str(discnum) )
	exec_dbase(dbq)		

```

The output in generated doxygen file is as follows:

```

def dbase.dbase_process.update_score_tags  	(  	   	 album_name,
		  	artist_name,
		  	discnum	 
	) 			

Get scores from ablum copied over and increase by one.

Parameters:
    	album_name 	Name of album
    	artist_name 	Name of artist
    	discnum 	Disc number of album

A query is sent to query_dbase function to get the score of album using passed parameters. The score is extracted by passed query results then increased by 1. The album is updated with new score 

```

The problem is that this code does not show up:

```

	# Set sqlite query into dbq with passed parameters.
        # Pass query to query_dbase where results will be returned into
        # into old_album_score
       # Set query to set album score to new value and pass to exec_dbase
        # so sqlite database is updated.

```

I can put it in the header as notes or details but is it possible to get them to show in doxygen generated file just by the comments in the body?

---

