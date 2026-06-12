---
title: "Where to get WebUtils from??"
date: 2009-07-12
forum: Programming Talk
---

### Post by UbuKunubi on 2009-07-12
Hi Folks!

I've run into an example Python program that makes use of WebUtils.

The problem I've hit is that (with google) I can find a LOT of links to pages talking about WebUtils, but I cant find a download page for it.

And I've also searched ALL of the Ubuntuforums, but I could only find 1 link to a mac/email issue that was irrelevant to me.

Can anyone please point me in the right direction?

Many thanks,
Ubu

---

### Post by durand on 2009-07-12
What is the example program? Maybe it bundles webutils with it?

EDIT: It's the webkit bindings for python.

---

### Post by UbuKunubi on 2009-07-12
> **durand said:**
> What is the example program? Maybe it bundles webutils with it?

EDIT: It's the webkit bindings for python.

Here is the example - sorry I dont have a link to where it came from.
[code]
#!/usr/bin/env python
# -*- coding: iso8859-1 -*-

# Copyright (C) 2006/09/20-25, Akshay Gattani <agattani AT sfu DOT ca)
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#

#General Description:
"""
This is a python client to collect all headlines and news stories (content) related to
a single event from all major newspaper/media websites such as: NY Times, BBC,
Reuters, Washington Post, etc

The client uses the combined strengths of python modules and libraries like urllib2, beautiful soup,
feedparser, WebUtils and re.

Author: Akshay Gattani

Explaination of some common terminology being used
"event" : Any current event/news being followed at news.google
"newssources": Newspapers/media majors that typically follow any news story
"domain": news at google is generally divided into domains like world, tech, health etc
"""

from BeautifulSoup import BeautifulSoup          # For processing HTML
from BeautifulSoup import BeautifulStoneSoup     # For processing XML
from WebUtils.Funcs import *					 # For HTML and ASCII encodings
from time import sleep							 # For making the script sleep
from operator import itemgetter					 # For Dictionary sorting headaches!
from extract import TemplatetNewsExtractor 		 # To extract news from sources
import BeautifulSoup                             # To get everything
import urllib2
import re
import feedparser
import string
import os
import sys
import codecs

#common regular expressions
#Remember shortest possible matches and NOT longest possible ones
#Hence add a ? after .*
reNonAscii 	= re.compile( '&.*?;' )
reTags		= re.compile( '<.*?>' )
reSpace		= re.compile( '&nbsp;' )
reApostrophe = re.compile( '&#39;' )

#Ordering of substitutions
#d4 = reNonAscii.sub( "", reApostrophe.sub( "'", reSpace.sub( " ", reTags.sub( "", d ) ) ) )

#Creating global instance of news extractor
extractor = TemplatetNewsExtractor()

#Cut off for number of news stories
newsCutOff = 0
#Global Sources Name List
globalSourcesList =	[
					"WashingtonPostUnitedStates",	
					"Reuters",
					"Bloomberg",
					"GuardianUnlimitedUK",
					"InternationalHeraldTribuneFrance",
					"DailyTelegraphAustralia",
					"CBSNewsNewYork",
					"ABCNews",
					"HoustonChronicleUnitedStates",
					"SanJoseMercuryNewsUSA",
					"MonstersandCriticscomUK",
					"CBS11TX",
					"Forbes",
					"WyomingNewsWY",
					"abc7newscomCA",
					"NewsObserverNC",
					"NaplesDailyNewsFL",
					"WashingtonTimesDC",
					"TownHallDC"
					]  
					#please add any other news sources here and
					#take care that a corresponding extractor function is added in extract.py
					#DallasMorningNewssubscriptionTX
					
class GoogleNewsReader:
	def getLinksForStories( self, url ):
		"""	Retrieves all the links for the '20' news stories for each domain.
		Caution: This method has a lot of data hard coded, like string indexes where links need to be extracted etc"""
	
		linkTuple = []
		try:
			req = urllib2.Request( url, None, headers = {'User-agent':'Mozilla/5.0'} )
			page = urllib2.urlopen( req ).read()
			soup = BeautifulSoup.BeautifulSoup( page )
		except urllib2.URLError, urllib2.HTTPException:
			#Continue for loop without abruptly stopping
			return []
			
		for i,html in zip( soup.findAll('title')[2:], soup.findAll('description')[1:] ):
			
			# focus on attribute class=p href within the description field
			htmlSoup = BeautifulSoup.BeautifulSoup( str(html) )
			linkAllRegex = re.compile( "&lt;a class=p href.*&gt;" )
			# dont have space between all and .*
			allNumNewsArticlesRegex = re.compile( "&lt;b&gt;all.*&lt;/b&gt;" )
			numRegex = re.compile( "[\d,]+" )
			
			linkStr = linkAllRegex.findall( str(html) )
			for link in linkStr:

				linkEndTagLoc = string.find( link, "&gt;" )
				#19 is always the index location where the link string starts from
				url = str( link[19:linkEndTagLoc] )
				#!!!Important to add a filter so that search results are not restricted
				noFilterUrl = "%s%s" % (url, "&filter=0" )

				#Also try and extract the total number of stories it says each event has from different sources
				#The format for regex is something like this
				#<b>all ??? news articles</b>

				allNewsArticlesStr = allNumNewsArticlesRegex.findall( link )
				noOfNewsStories = int( replaceCommaInInt( numRegex.findall(  str( allNewsArticlesStr[0]) )[0] ) )	
				linkTuple.append( (htmlDecode(noFilterUrl), noOfNewsStories ) )
		return linkTuple
								  

#Common Functions, mostly string manipulation
def replaceCommaInInt( strDec ):
	return string.replace( strDec, ",", "" )

def extractSourceName( sourceName ):
	subre = re.compile(r"[^A-Za-z0-9]").sub
	subSourceString = subre("", sourceName)
	return subSourceString

def getSourceFunctionString( sourceNameWithSpChars ):
	subre = re.compile(r"[^A-Za-z0-9]").sub
	subSourceString = subre("", sourceNameWithSpChars)
	return subSourceString

def postProcessAndCondense( extractP ):
	pp = []
	for i in range( len(extractP) ):
		p = reNonAscii.sub( "", reApostrophe.sub( "'", reSpace.sub( " ", reTags.sub( "", str(extractP[i]) ) ) ) )
		pp.append( p )
	return string.join( pp )

def extractWrapper( sourceName, newsLink, ):
	callingExtractFunc = "extract_%s" % extractSourceName( sourceName )
	try:
		req = urllib2.Request( newsLink , None, headers = {'User-agent':'Mozilla/5.0'} )
		page = urllib2.urlopen( req ).read()
	except urllib2.URLError, urllib2.HTTPException:
		return ""
	soup = BeautifulSoup.BeautifulSoup( page )
	try:
		extractP = getattr( extractor, callingExtractFunc)( soup )
	except IndexError, AttributeError:
		return ""
	if extractP == []:
		return ""
	else:
		return postProcessAndCondense( extractP )
						

#A hash (Dictionary) to indicate what sources have been consumed
# Always initialize all entries to 0 before we read a news thread		
def initializeGlobalSourcesDict( ):
	flagSourcesDict = {}
	for i in globalSourcesList:
		flagSourcesDict[i] = 0
	return flagSourcesDict

def estimateNewsSourcesFrequency( trialUrlSet, linksDict ):
	"""Estimates what the top news sources (that report most news stories) for each domain"""
	print "\nEstimation in Progress.... for %s\n" % trialUrlSet[0][0]
	loopCount = 0
	for (domain, url) in trialUrlSet:
		sourcesEstimate = {}
		for (newsEventLink, countOfNewsSources) in linksDict[domain]:
			#if loopCount < 5:
			#	loopCount += 1
			#else:
			#	break

			# print newsEventLink, countOfNewsSources
			# newsEvent is a sequence organized as
			# (newsEvent1-link, Count-Of-News-Sources reporting the news1)
			# (newsEvent1-link, Count-Of-News-Sources reporting the news2,..)

			#To iterate over multiple NEXT enabled pages
			if countOfNewsSources < 100:
				#we dont process a news story which has less than 500 sources
				continue

			nextPageCount = 0
			try:
				req = urllib2.Request( newsEventLink, None, headers = {'User-agent':'Mozilla/5.0'} )
				page = urllib2.urlopen( req ).read()
				soup = BeautifulSoup.BeautifulSoup( page )
			except urllib2.URLError, urllib2.HTTPException:
				#Continue for loop without abruptly stopping
				continue

			while( nextPageCount < countOfNewsSources-100):
				# print soup.prettify()
				# template match for this
				# font color=#6f6f6f
				attrs = {}
				attrs['color'] = "#6f6f6f"
				sourcesList = soup.findAll('font', attrs)
				for i in range( len(sourcesList)-1):
					# Now separately extract title and news source name
					sourceName = str(sourcesList[i].string).replace( "&nbsp", " " )[:-2]
					# print "SourceName: %s" % sourceName
					if sourceName not in sourcesEstimate.keys():
						sourcesEstimate[sourceName] = 1
					else:
						sourcesEstimate[sourceName] += 1

				nextPageCount += 30
				nextNewsEventLink = newsEventLink+"&sa=N&start="+str(nextPageCount)
				try:
					req = urllib2.Request( nextNewsEventLink, None, headers = {'User-agent':'Mozilla/5.0'} )
					page = urllib2.urlopen( req ).read()
					soup = BeautifulSoup.BeautifulSoup( page )
				except urllib2.URLError, urllib2.HTTPException:
					#Continue for loop without abruptly stopping
					continue

		#print "No of Stories Covered: %d" % len(linksDict[domain])
		itemsSourcesEstimate = sourcesEstimate.items()
		itemsSourcesEstimate.sort(key = itemgetter(1), reverse=True)
		#print "Most common Sources that cover news Stories: \n"
		#for i in range( len(itemsSourcesEstimate) ):
			#print itemsSourcesEstimate[i][0].encode( 'ascii', 'replace' ), ": ", itemsSourcesEstimate[i][1]
			#print itemsSourcesEstimate[i][0], ": ", itemsSourcesEstimate[i][1]
		return itemsSourcesEstimate

def extractAndStoreDomainNews( trialUrlSet, linksDict ):
	"""Extracts and stores news from a particular domain into newsData/$domain folder"""
	print "\nExtraction in Progress.... for %s\n" % trialUrlSet[0][0]
	print "------------------------\n"
	print "EXTRACTION LOG\n"
	print "------------------------\n"
	loopCount = 0
	for (domain, url) in trialUrlSet:
		for itr in range( len(linksDict[domain]) ):
			(newsEventLink, countOfNewsSources)	= linksDict[domain][itr]
			if domain not in os.listdir("newsData"):
				os.mkdir( "%s/%s" % ("newsData", domain ) ) 
			print "No of Sources: %d, Output-File: %s/%s/story%d.txt"  %( countOfNewsSources, "newsData", domain, itr )

			# print newsEventLink, countOfNewsSources
			# linksDict[domain] is a sequence organized as (newsEvent-link, Count-Of-News-Sources reporting the news)

			#we dont process a news story which has less than 100 sources for reliability
			if countOfNewsSources < 100:
				#continue with the next story link
				continue

			#storgae & extraction related initializations
			#fStory = codecs.open( "%s/%s/story%d.txt" % ("newsData", domain, itr), "w", "ISO-8859-1", "replace"  )
			#fTitle = codecs.open( "%s/%s/title%d.txt" % ("newsData", domain, itr), "w", "ISO-8859-1", "replace"  )
			fStory = open( "%s/%s/story%d.txt" % ("newsData", domain, itr), "wr"  )
			fTitle = open( "%s/%s/title%d.txt" % ("newsData", domain, itr), "wr"  )
			countTillCutOff = 0
			globalSourcesDict = initializeGlobalSourcesDict()

			nextPageCount = 0
			try:
				req = urllib2.Request( newsEventLink, None, headers = {'User-agent':'Mozilla/5.0'} )
				page = urllib2.urlopen( req ).read()
				soup = BeautifulSoup.BeautifulSoup( page )
			except urllib2.URLError, urllib2.HTTPException:
				#Continue for loop without abruptly stopping
				print "error on news story - %d" % itr
				continue

			#last page may have some special cases.. consider later		
			while( nextPageCount < countOfNewsSources and countTillCutOff < newsCutOff):
				# template match for this
				# <div class=mainbody>
				#extract all <ahref> 's after that
				attrs = {}
				attrs['class'] = "mainbody"
				tagName = 'div'
				#if theres an error on the page, skip to next 30
				try:
					sourcesList1 = soup.findAll(tagName, attrs)
					sourcesList2 = sourcesList1[0].findAllNext( 'a' )
				except IndexError:
					print "error on news story - %d" % itr
					print "\terror at news Page count - %d" % nextPageCount
					nextPageCount += 30
					continue

				countTill30 = 0
				for i in range( len(sourcesList2)):
					# Now separately extract title, newsLink and news source name
					# For source name match
					# font color=#6f6f6f
					if sourcesList2[i].string is None:
							continue
					else:
						countTill30 += 1

					#End of page
					if countTill30 > 30 or sourcesList2[i].string[0:5] == "About":
						break

					attrs = {}
					attrs["color"]= "#6f6f6f"
					sourceNameList = sourcesList2[i].findNext('font', attrs)
					sourceName = str(sourceNameList.string).replace( "&nbsp", " " )[:-2]

					newsLink = htmlDecode( sourcesList2[i].attrs[0][1] )
					newsTitle = htmlDecode( sourcesList2[i].string )
					#Output all headlines together
					fTitle.write( "<Title>\n" )
					try:
						fTitle.write( newsTitle )
					except UnicodeEncodeError:
						fTitle.write( newsTitle.encode( 'ascii', 'ignore' ) )
					fTitle.write( "\n" )
					fTitle.write( "</Title>\n" )

					if extractSourceName( sourceName ) in globalSourcesList and globalSourcesDict[extractSourceName(sourceName)] == 0:
						newsContent = extractWrapper( sourceName, newsLink )
						#print "CONTENT:\n"
						#print newsContent
					else:
						continue

					if newsContent != "":
						print extractSourceName( sourceName ), newsTitle, newsLink
						globalSourcesDict[extractSourceName(sourceName)] = 1
						fStory.write( "<Title>\n" )
						try:
							fStory.write( newsTitle )
						except UnicodeEncodeError:
							fStory.write( newsTitle.encode( 'ascii', 'ignore' ) )
						fStory.write( "\n" )
						fStory.write( "</Title>\n" )

						fStory.write( "<Source>\n" )
						try:
							fStory.write( sourceName )
						except UnicodeEncodeError:
							fStory.write( sourceName.encode( 'ascii', 'ignore' ) )
						fStory.write( "\n" )
						fStory.write( "</Source>\n" )

						fStory.write( "<Story>\n" )
						try:
							fStory.write( newsContent )
						except UnicodeEncodeError:
							fStory.write( newsContent.encode( 'ascii', 'ignore' ) )

						fStory.write( "\n" )
						fStory.write( "</Story>\n" )

						fStory.write( "\n" )
						countTillCutOff += 1

					#This breaks out of inner for loop, still need to break out of while loop
					if countTillCutOff >= newsCutOff:
						break

				#print "\n"
				if countTillCutOff >= newsCutOff:
					break

				nextPageCount += 30
				nextNewsEventLink = newsEventLink+"&sa=N&start="+str(nextPageCount)
				try:
					req = urllib2.Request( nextNewsEventLink, None, headers = {'User-agent':'Mozilla/5.0'} )
					page = urllib2.urlopen( req ).read()
					soup = BeautifulSoup.BeautifulSoup( page )
				except urllib2.URLError, urllib2.HTTPException:
					#Continue for loop without abruptly stopping
					continue
			fStory.close()
			#Now if the count is less than 5 you delete the file since it pretty useless
			if countTillCutOff < newsCutOff:
				os.remove( "%s/%s/story%d.txt" % ("newsData", domain, itr) )
				os.remove( "%s/%s/title%d.txt" % ("newsData", domain, itr) )
				print "RESULT: File deleted since there are only %d sources" % countTillCutOff
			else:
				print "RESULT: File accepted with %d news stories" % newsCutOff
			#Also gather all headlines if you can.
			print "\n"	
		#iteration over news stories ends here
	#iteration over domains ends here
	return		

#Execution of Script starts here
if __name__ == '__main__':

	allOrSingleFlag = sys.argv[1]
	newsCutOff = int(sys.argv[2])
	print "No of stories cut off is %d" % newsCutOff
	# 1.Basic setting to open main google.news rss feed (world, US, Business, Tech, Sports, Entertainment, Health)
	permUrlSet = [ ("world", "http://news.google.com/nwshp?ned=us&topic=w&output=rss"),
		   ("us", 	"http://news.google.com/nwshp?ned=us&topic=n&output=rss"),
		   ("business", "http://news.google.com/nwshp?ned=us&topic=b&output=rss"),
		   ("tech", 	"http://news.google.com/nwshp?ned=us&topic=t&output=rss"),
		   ("sports", 	"http://news.google.com/nwshp?ned=us&topic=s&output=rss"),
		   ("entertainment","http://news.google.com/nwshp?ned=us&topic=e&output=rss"),
		   ("health", 	"http://news.google.com/nwshp?ned=us&topic=m&output=rss"),
		   ("popular", 	"http://news.google.com/nwshp?ned=us&topic=po&output=rss")]

	trialWorldSet = [( "world","http://news.google.com/nwshp?ned=us&topic=w&output=rss") ]
	trialUsSet = [( "us","http://news.google.com/nwshp?ned=us&topic=n&output=rss") ]
	trialBusinessSet = [( "business","http://news.google.com/nwshp?ned=us&topic=b&output=rss") ]
	trialTechSet = [( "tech","http://news.google.com/nwshp?ned=us&topic=t&output=rss") ]
	trialSportsSet = [( "sports","http://news.google.com/nwshp?ned=us&topic=s&output=rss") ]
	trialEntSet = [( "entertainment","http://news.google.com/nwshp?ned=us&topic=e&output=rss") ]
	trialHealthSet = [( "health","http://news.google.com/nwshp?ned=us&topic=m&output=rss") ]
	trialPopularSet = [("popular", "http://news.google.com/nwshp?ned=us&topic=po&output=rss")]

	trialDict = {}
	trialDict["world"] = [( "world","http://news.google.com/nwshp?ned=us&topic=w&output=rss") ]
	trialDict["us"] = [( "us","http://news.google.com/nwshp?ned=us&topic=n&output=rss") ]
	trialDict["business"] = [( "business","http://news.google.com/nwshp?ned=us&topic=b&output=rss") ]
	trialDict["tech"] = [( "tech","http://news.google.com/nwshp?ned=us&topic=t&output=rss") ]
	trialDict["sports"] = [( "sports","http://news.google.com/nwshp?ned=us&topic=s&output=rss") ]
	trialDict["entertainment"] = [( "entertainment","http://news.google.com/nwshp?ned=us&topic=e&output=rss") ]
	trialDict["health"] = [( "health","http://news.google.com/nwshp?ned=us&topic=m&output=rss") ]
	trialDict["popular"] = [("popular", "http://news.google.com/nwshp?ned=us&topic=po&output=rss")]

	if str(allOrSingleFlag) == "all":
		domainSet = permUrlSet
	else:
		domainSet = trialDict[ str(allOrSingleFlag) ]

	linksDict = {}	
	for (domain, url) in domainSet:
		rssReader = GoogleNewsReader()
		linksDict[domain] = rssReader.getLinksForStories( url )

	#5. Extract and Store news from sources
	#Tested works!
	#domain = "us"
	#url = "http://news.google.com/?ned=us&topic=n&output=rss"
	#linksDict = {}
	#linksDict["us"] = []
	#trialUrl = "http://news.google.com/?ned=us&filter=0&ncl=http://www.mtv.com/news/articles/1541437/20060921/index.jhtml%3Fheadlines%3Dtrue&hl=en&filter=0"
	#linksDict["us"].append( (htmlDecode(trialUrl), 246 ) )

	extractAndStoreDomainNews( domainSet, linksDict )
[/code

---

### Post by durand on 2009-07-12
I was wrong about it being from webkit. It's actually part of a suite of python bindings called webware for python: [http://www.webwareforpython.org/](http://www.webwareforpython.org/) It doesn't seem to be in the repositories so you will need to install it manually from that site.

---

### Post by UbuKunubi on 2009-07-13
> **durand said:**
> I was wrong about it being from webkit. It's actually part of a suite of python bindings called webware for python: [http://www.webwareforpython.org/](http://www.webwareforpython.org/) It doesn't seem to be in the repositories so you will need to install it manually from that site.

Thank you!

Thats a great site - not sure how I've not found it before?
All the best,
Ubu

---

### Post by durand on 2009-07-13
It does look like a good set of modules but I think you may be better off using something like [Django]("http://djangoproject.org") for web applications.

---

