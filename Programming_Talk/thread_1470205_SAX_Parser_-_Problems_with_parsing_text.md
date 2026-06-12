---
title: "SAX Parser - Problems with parsing text"
date: 2010-05-02
forum: Programming Talk
---

### Post by jit.sd on 2010-05-02
Hey , 

Am trying to use a SAX Parser to parse an XML file. Its working fine for all the tags that I need except the <BODY> tag. I have no idea why. Would be very grateful if someone could have a look at it and point me in the right direction, thank you. 

Currently I am extracting TOPICS, and REUTERS attributes and they are working perfectly. Only problem with extracting <BODY> attributes. 

Jit

```

import java.io.IOException;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

import javax.xml.parsers.ParserConfigurationException;
import javax.xml.parsers.SAXParser;
import javax.xml.parsers.SAXParserFactory;

import org.xml.sax.Attributes;
import org.xml.sax.SAXException;

import org.xml.sax.helpers.DefaultHandler;

public class ParseTest extends DefaultHandler
{
	private String tempVal;
	private List topics;
	private static int inTopics;
	
	// Event Handlers
	public void startElement(String uri,String localName, String qName,Attributes attributes) throws SAXException
	{
		tempVal="";
		if (qName.equalsIgnoreCase("REUTERS"))
		{
			System.out.println("NEWID : "+attributes.getValue("NEWID"));
			System.out.println("LEWISSPLIT : "+attributes.getValue("LEWISSPLIT"));
			System.out.println("TOPICS : "+attributes.getValue("TOPICS"));
		}
		else if (qName.equalsIgnoreCase("TOPICS"))
		{
			inTopics=1;
			/*
			if (!(topics.isEmpty()))
			{
				topics.clear();
			}
			*/
		}
		
	}
	
	public void characters(char[] ch, int start, int length) throws SAXException 
	{
		tempVal = new String(ch,start,length);
	}
	
	public void endElement(String uri,String localName,String qName) throws SAXException
	{
		if (qName.equalsIgnoreCase("D"))
		{	
			//topics.add(tempVal);
			if(inTopics==1)
			{
				System.out.println(tempVal);
			}
		}
		else if (qName.equalsIgnoreCase("TOPICS"))
		{
			inTopics=0;
			/*
			System.out.print("TOPICS ");
			Iterator it = topics.iterator();
			while (it.hasNext())
			{
				System.out.print(": "+(it.next().toString()));
			}
			System.out.print("\n");
			*/
		}
		else if(qName.equalsIgnoreCase("BODY"))
		{
			System.out.println("BODY : "+tempVal);
			System.out.print("\n");
		}
	}
	
	
	public static void main(String[] args)
	{
		ParseTest pt=new ParseTest();
		SAXParserFactory spf = SAXParserFactory.newInstance();
		inTopics=0;
		
		try
		{
			SAXParser sp= spf.newSAXParser();
			sp.parse("example.xml",pt);
		}
		catch(SAXException se) 
		{
			se.printStackTrace();
		}
		catch(ParserConfigurationException pce) 
		{
			pce.printStackTrace();
		}
		catch (IOException ie) 
		{
			ie.printStackTrace();
		}
		
		
		
	}
}

```

This is a part of my XML file. 

```

<?xml version="1.0"?>
<LEWIS>
<REUTERS TOPICS="YES" LEWISSPLIT="TRAIN" CGISPLIT="TRAINING-SET" OLDID="5544" NEWID="1">
<DATE>26-FEB-1987 15:01:01.79</DATE>
<TOPICS><D>cocoa</D></TOPICS>
<PLACES><D>el-salvador</D><D>usa</D><D>uruguay</D></PLACES>
<PEOPLE></PEOPLE>
<ORGS></ORGS>
<EXCHANGES></EXCHANGES>
<COMPANIES></COMPANIES>
<UNKNOWN> 
C T
f0704reute
u f BC-BAHIA-COCOA-REVIEW   02-26 0105</UNKNOWN>
<TEXT>
<TITLE>BAHIA COCOA REVIEW</TITLE>
<DATELINE>    SALVADOR, Feb 26 - </DATELINE><BODY>Showers continued throughout the week in
the Bahia cocoa zone, alleviating the drought since early
January and improving prospects for the coming temporao,
although normal humidity levels have not been restored,
Comissaria Smith said in its weekly review.
    The dry period means the temporao will be late this year.
    Arrivals for the week ended February 22 were 155,221 bags
of 60 kilos making a cumulative total for the season of 5.93
mln against 5.81 at the same stage last year. Again it seems
that cocoa delivered earlier on consignment was included in the
arrivals figures.
    Comissaria Smith said there is still some doubt as to how
much old crop cocoa is still available as harvesting has
practically come to an end. With total Bahia crop estimates
around 6.4 mln bags and sales standing at almost 6.2 mln there
are a few hundred thousand bags still in the hands of farmers,
middlemen, exporters and processors.
    There are doubts as to how much of this cocoa would be fit
for export as shippers are now experiencing dificulties in
obtaining +Bahia superior+ certificates.
    In view of the lower quality over recent weeks farmers have
sold a good part of their cocoa held on consignment.
    Comissaria Smith said spot bean prices rose to 340 to 350
cruzados per arroba of 15 kilos.
    Bean shippers were reluctant to offer nearby shipment and
only limited sales were booked for March shipment at 1,750 to
1,780 dlrs per tonne to ports to be named.
    New crop sales were also light and all to open ports with
June/July going at 1,850 and 1,880 dlrs and at 35 and 45 dlrs
under New York july, Aug/Sept at 1,870, 1,875 and 1,880 dlrs
per tonne FOB.
    Routine sales of butter were made. March/April sold at
4,340, 4,345 and 4,350 dlrs.
    April/May butter went at 2.27 times New York May, June/July
at 4,400 and 4,415 dlrs, Aug/Sept at 4,351 to 4,450 dlrs and at
2.27 and 2.28 times New York Sept and Oct/Dec at 4,480 dlrs and
2.27 times New York Dec, Comissaria Smith said.
    Destinations were the U.S., Covertible currency areas,
Uruguay and open ports.
    Cake sales were registered at 785 to 995 dlrs for
March/April, 785 dlrs for May, 753 dlrs for Aug and 0.39 times
New York Dec for Oct/Dec.
    Buyers were the U.S., Argentina, Uruguay and convertible
currency areas.
    Liquor sales were limited with March/April selling at 2,325
and 2,380 dlrs, June/July at 2,375 dlrs and at 1.25 times New
York July, Aug/Sept at 2,400 dlrs and at 1.25 times New York
Sept and Oct/Dec at 1.25 times New York Dec, Comissaria Smith
said.
    Total Bahia sales are currently estimated at 6.13 mln bags
against the 1986/87 crop and 1.06 mln bags against the 1987/88
crop.
    Final figures for the period to February 28 are expected to
be published by the Brazilian Cocoa Trade Commission after
carnival which ends midday on February 27.
 Reuter
</BODY></TEXT>
</REUTERS>
<REUTERS TOPICS="NO" LEWISSPLIT="TRAIN" CGISPLIT="TRAINING-SET" OLDID="5545" NEWID="2">
<DATE>26-FEB-1987 15:02:20.00</DATE>
<TOPICS></TOPICS>
<PLACES><D>usa</D></PLACES>
<PEOPLE></PEOPLE>
<ORGS></ORGS>
<EXCHANGES></EXCHANGES>
<COMPANIES></COMPANIES>
<UNKNOWN> 
F Y
f0708reute
d f BC-STANDARD-OIL-&lt;SRD>-TO   02-26 0082</UNKNOWN>
<TEXT>
<TITLE>STANDARD OIL &lt;SRD> TO FORM FINANCIAL UNIT</TITLE>
<DATELINE>    CLEVELAND, Feb 26 - </DATELINE><BODY>Standard Oil Co and BP North America
Inc said they plan to form a venture to manage the money market
borrowing and investment activities of both companies.
    BP North America is a subsidiary of British Petroleum Co
Plc &lt;BP>, which also owns a 55 pct interest in Standard Oil.
    The venture will be called BP/Standard Financial Trading
and will be operated by Standard Oil under the oversight of a
joint management committee.

 Reuter
</BODY></TEXT>
</REUTERS>
</LEWIS>

```

---

