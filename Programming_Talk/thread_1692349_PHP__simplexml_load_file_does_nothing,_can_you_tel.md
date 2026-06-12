---
title: "PHP  simplexml_load_file does nothing, can you tell me why?"
date: 2011-02-21
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-21
I would think it would according to php.net

first off I have to make an empty loc.xml file with permissions in order to write contents, I understand the permission idea.

secondly,  simplexml_load_file does nothing
I get it straight from here

[http://us2.php.net/manual/en/function.simplexml-load-file.php](http://us2.php.net/manual/en/function.simplexml-load-file.php)

[PHP]<?php
   $request='http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&startRecord=2&maximumRecords=5';
   //echo $request;
   $filename = dirname(__FILE__)."/loc.xml";
   $raw_xml = file_get_contents($request);
   //echo $raw_xml;
   $fp = fopen($filename, "w");
   fwrite($fp, $raw_xml);
   fclose ($fp);



// The file test.xml contains an XML document with a root element
// and at least an element /[root]/title.

if (file_exists($filename)) {
    $xml = simplexml_load_file($filename);
    
    print_r($xml);


} else {
    exit('Failed to open loc.xml.');
}


?>[/PHP]

---

### Post by sdowney717 on 2011-02-21
I modified and it reports an error 'Failed loading XML'
which is self evident!

[PHP]<?php
  // $request='http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&startRecord=2&maximumRecords=5';
   //echo $request;
 //  $filename = dirname(__FILE__)."/loc.xml";
 //  $raw_xml = file_get_contents($request);
   //echo $raw_xml;
  // $fp = fopen($filename, "w");
  // fwrite($fp, $raw_xml);
  // fclose ($fp);



// The file test.xml contains an XML document with a root element
// and at least an element /[root]/title.

libxml_use_internal_errors(true);
$filename = dirname(__FILE__)."/loc.xml";
if (file_exists($filename)) {
    $xml = simplexml_load_file($filename);
    if ($xml == FALSE){
      echo "Failed loading XML\n";
      foreach(libxml_get_errors() as $error) {echo "\t", $error->message;}//Failed loading XML was the returned error 
    }
    print_r($xml);


} else {
    exit('Failed to open loc.xml.');
}


?>
[/PHP]

this is the xml file that is coming back form LOC
[PHP]<?xml version="1.0"?>
<zs:searchRetrieveResponse xmlns:zs="http://www.loc.gov/zing/srw/"><zs:version>1.1</zs:version><zs:numberOfRecords>2144</zs:numberOfRecords><zs:records><zs:record><zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema><zs:recordPacking>xml</zs:recordPacking><zs:recordData><record xmlns="http://www.loc.gov/MARC21/slim">
  <leader>01026ngm a22002773a 4500</leader>
  <controlfield tag="001">16429180</controlfield>
  <controlfield tag="005">20100823131409.0</controlfield>
  <controlfield tag="007">vffcjaho|</controlfield>
  <controlfield tag="008">100823s2010    xxu060            mleng  </controlfield>
  <datafield tag="906" ind1=" " ind2=" ">
    <subfield code="a">0</subfield>
    <subfield code="b">cbc</subfield>
    <subfield code="c">orignew</subfield>
    <subfield code="d">u</subfield>
    <subfield code="e">ncip</subfield>
    <subfield code="f">20</subfield>
    <subfield code="g">y-movingim</subfield>
  </datafield>
  <datafield tag="955" ind1=" " ind2=" ">
    <subfield code="b">qm12 2010-08-23</subfield>
  </datafield>
  <datafield tag="010" ind1=" " ind2=" ">
    <subfield code="a">  2010608899</subfield>
  </datafield>
  <datafield tag="017" ind1=" " ind2=" ">
    <subfield code="a">PA0001684303</subfield>
    <subfield code="b">U.S. Copyright Office</subfield>
  </datafield>
  <datafield tag="040" ind1=" " ind2=" ">
    <subfield code="a">DLC</subfield>
    <subfield code="c">DLC</subfield>
    <subfield code="e">amim</subfield>
  </datafield>
  <datafield tag="050" ind1="0" ind2="0">
    <subfield code="a">VBU 4599 (viewing copy)</subfield>
  </datafield>
  <datafield tag="245" ind1="0" ind2="0">
    <subfield code="a">30 Rock.</subfield>
    <subfield code="p">Emmanuelle goes to Dinosaur Land.</subfield>
  </datafield>
  <datafield tag="246" ind1="3" ind2="0">
    <subfield code="a">Emmanuelle goes to Dinosaur Land</subfield>
  </datafield>
  <datafield tag="246" ind1="3" ind2=" ">
    <subfield code="a">Thirty rock.</subfield>
    <subfield code="p">Emmanuelle goes to Dinosaur Land</subfield>
  </datafield>
  <datafield tag="257" ind1=" " ind2=" ">
    <subfield code="a">United States.</subfield>
  </datafield>
  <datafield tag="260" ind1=" " ind2=" ">
    <subfield code="c">2010-05-13.</subfield>
  </datafield>
  <datafield tag="300" ind1=" " ind2=" ">
    <subfield code="a">1 videocassette of 1 (Betacam SP) (60 min.) :</subfield>
    <subfield code="b">sd., col. ;</subfield>
    <subfield code="c">1/2 in.</subfield>
    <subfield code="3">viewing copy.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Episode no. 4021.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Sources used: videocassette container; Copyright catalog online; Copyright description.</subfield>
  </datafield>
  <datafield tag="655" ind1=" " ind2="0">
    <subfield code="a">Situation comedies (Television programs)</subfield>
  </datafield>
  <datafield tag="655" ind1=" " ind2="0">
    <subfield code="a">Fiction television programs.</subfield>
  </datafield>
  <datafield tag="710" ind1="2" ind2=" ">
    <subfield code="a">Copyright Collection (Library of Congress)</subfield>
    <subfield code="5">DLC</subfield>
  </datafield>
</record></zs:recordData><zs:recordPosition>2</zs:recordPosition></zs:record><zs:record><zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema><zs:recordPacking>xml</zs:recordPacking><zs:recordData><record xmlns="http://www.loc.gov/MARC21/slim">
  <leader>01718cjm a22003971a 4500</leader>
  <controlfield tag="001">13463061</controlfield>
  <controlfield tag="005">20051217130827.0</controlfield>
  <controlfield tag="007">sd fsngnnmmned</controlfield>
  <controlfield tag="008">040120r19961983caurcn              eng d</controlfield>
  <datafield tag="024" ind1="1" ind2=" ">
    <subfield code="a">076744000422</subfield>
  </datafield>
  <datafield tag="035" ind1=" " ind2=" ">
    <subfield code="a">(DLC)   2004567544</subfield>
  </datafield>
  <datafield tag="040" ind1=" " ind2=" ">
    <subfield code="a">KFW</subfield>
    <subfield code="c">KFW</subfield>
    <subfield code="d">IEP</subfield>
    <subfield code="d">OCLCQ</subfield>
    <subfield code="d">DLC</subfield>
  </datafield>
  <datafield tag="020" ind1=" " ind2=" ">
    <subfield code="c">$17.98</subfield>
  </datafield>
  <datafield tag="024" ind1="1" ind2="0">
    <subfield code="a">076744000422</subfield>
  </datafield>
  <datafield tag="028" ind1="0" ind2="2">
    <subfield code="a">HIPD 40004</subfield>
    <subfield code="b">Hip-O Records</subfield>
  </datafield>
  <datafield tag="028" ind1="0" ind2="2">
    <subfield code="a">40004-2</subfield>
    <subfield code="b">Hip-O Records</subfield>
  </datafield>
  <datafield tag="035" ind1=" " ind2=" ">
    <subfield code="a">(OCoLC)ocm35640234 </subfield>
  </datafield>
  <datafield tag="028" ind1="0" ind2="2">
    <subfield code="a">HIPD-40004</subfield>
    <subfield code="b">Hip-O Records</subfield>
  </datafield>
  <datafield tag="010" ind1=" " ind2=" ">
    <subfield code="a">  2004567544</subfield>
  </datafield>
  <datafield tag="042" ind1=" " ind2=" ">
    <subfield code="a">lcderive</subfield>
  </datafield>
  <datafield tag="050" ind1="0" ind2="0">
    <subfield code="a">SDA 85496</subfield>
  </datafield>
  <datafield tag="245" ind1="0" ind2="4">
    <subfield code="a">The '80s hit(s) back!</subfield>
    <subfield code="h">[sound recording].</subfield>
  </datafield>
  <datafield tag="246" ind1="3" ind2=" ">
    <subfield code="a">Eighty's hit(s) back!</subfield>
  </datafield>
  <datafield tag="260" ind1=" " ind2=" ">
    <subfield code="a">Universal City, Calif. :</subfield>
    <subfield code="b">Hip-O Records,</subfield>
    <subfield code="c">p1996.</subfield>
  </datafield>
  <datafield tag="300" ind1=" " ind2=" ">
    <subfield code="a">1 sound disc :</subfield>
    <subfield code="b">digital ;</subfield>
    <subfield code="c">4 3/4 in.</subfield>
  </datafield>
  <datafield tag="511" ind1="0" ind2=" ">
    <subfield code="a">Various performers.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Selections previously released 1983-1988.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Compact disc.</subfield>
  </datafield>
  <datafield tag="505" ind1="0" ind2=" ">
    <subfield code="a">She drives me crazy (Fine Young Cannibals) -- Walk the dinosaur (Was (Not Was)) -- You keep me hangin' on (Kim Wilde) -- The safety dance (Men Without Hats) -- Walking on sunshine (Katrina &amp; The Waves) -- One thing leads to another (The Fixx) -- Heaven is a place on earth (Belinda Carlisle) -- Everybody have fun tonight (Wang Chung) -- Cruel summer (Bananarama) -- Weird science (Oingo Boingo) -- Axel F (Harold Faltermeyer) -- The future's so bright, I gotta wear shades (Timbuk 3).</subfield>
  </datafield>
  <datafield tag="650" ind1=" " ind2="0">
    <subfield code="a">Rock music</subfield>
    <subfield code="y">1981-1990.</subfield>
  </datafield>
  <datafield tag="655" ind1=" " ind2="7">
    <subfield code="a">Compact discs.</subfield>
    <subfield code="2">lcsh</subfield>
  </datafield>
  <datafield tag="906" ind1=" " ind2=" ">
    <subfield code="a">7</subfield>
    <subfield code="b">cbc</subfield>
    <subfield code="c">copycat</subfield>
    <subfield code="d">3</subfield>
    <subfield code="e">ncip</subfield>
    <subfield code="f">20</subfield>
    <subfield code="g">y-genmusic</subfield>
  </datafield>
  <datafield tag="925" ind1="0" ind2=" ">
    <subfield code="a">acquire</subfield>
    <subfield code="b">2 copies</subfield>
    <subfield code="x">policy default</subfield>
  </datafield>
  <datafield tag="952" ind1=" " ind2=" ">
    <subfield code="a">muzerec</subfield>
  </datafield>
  <datafield tag="955" ind1=" " ind2=" ">
    <subfield code="a">vn76 2004-01-20 to MBRS/RS</subfield>
    <subfield code="e">vn76 2004-01-20 copy 2 to MBRS/RS</subfield>
  </datafield>
  <datafield tag="985" ind1=" " ind2=" ">
    <subfield code="c">OCLC</subfield>
    <subfield code="e">srreplace 2005-08</subfield>
  </datafield>
</record></zs:recordData><zs:recordPosition>3</zs:recordPosition></zs:record><zs:record><zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema><zs:recordPacking>xml</zs:recordPacking><zs:recordData><record xmlns="http://www.loc.gov/MARC21/slim">
  <leader>01461ngm a22003375a 4500</leader>
  <controlfield tag="001">11624471</controlfield>
  <controlfield tag="005">00000000000000.0</controlfield>
  <controlfield tag="008">930921s1967    xxu               vaeng  </controlfield>
  <datafield tag="035" ind1=" " ind2=" ">
    <subfield code="9">(DLC)   93513624</subfield>
  </datafield>
  <datafield tag="906" ind1=" " ind2=" ">
    <subfield code="a">0</subfield>
    <subfield code="b">ibc</subfield>
    <subfield code="c">orignew</subfield>
    <subfield code="d">u</subfield>
    <subfield code="e">ncip</subfield>
    <subfield code="f">19</subfield>
    <subfield code="g">y-movingim</subfield>
  </datafield>
  <datafield tag="010" ind1=" " ind2=" ">
    <subfield code="a">   93513624 </subfield>
  </datafield>
  <controlfield tag="007">v| ||||||</controlfield>
  <datafield tag="017" ind1=" " ind2=" ">
    <subfield code="a">PA608-254</subfield>
    <subfield code="b">U.S. Copyright Office</subfield>
  </datafield>
  <datafield tag="040" ind1=" " ind2=" ">
    <subfield code="a">DLC</subfield>
    <subfield code="c">DLC</subfield>
    <subfield code="e">amim</subfield>
  </datafield>
  <datafield tag="050" ind1="0" ind2="0">
    <subfield code="a">VBK 2042 (viewing copy)</subfield>
  </datafield>
  <datafield tag="245" ind1="0" ind2="0">
    <subfield code="a">Abbott &amp; Costello cartoons.</subfield>
    <subfield code="p">Dinosaur Dilemna /</subfield>
    <subfield code="c">a Hanna-Barbera Production in association with RKO Pictures Company-Jomar Productions ; directed and produced by Joseph Barbera and William Hanna.</subfield>
  </datafield>
  <datafield tag="260" ind1=" " ind2=" ">
    <subfield code="a">United States :</subfield>
    <subfield code="b">[s.n.],</subfield>
    <subfield code="c">1967.</subfield>
  </datafield>
  <datafield tag="300" ind1=" " ind2=" ">
    <subfield code="a">1 videocassette of 1 :</subfield>
    <subfield code="b">sd., col. ;</subfield>
    <subfield code="c">3/4 in. viewing copy.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Copyright: PUB 5May67; PA608-254.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Copyright notice on film: RKO General Inc., Jomar Prod. Inc., Hanna-Barbera Productions, Inc. ; 1967.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">On cassette with episodes: Frigid fugitive ; Invader raider ; Paddleboat pirate.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Number 12</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Animation.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Source used: copyright data sheet.</subfield>
  </datafield>
  <datafield tag="541" ind1=" " ind2=" ">
    <subfield code="d">Received: 4/27/1993;</subfield>
    <subfield code="3">viewing copy;</subfield>
    <subfield code="c">copyright deposit--RNR;</subfield>
    <subfield code="a">Copyright Collection.</subfield>
  </datafield>
  <datafield tag="710" ind1="2" ind2=" ">
    <subfield code="a">Copyright Collection (Library of Congress)</subfield>
    <subfield code="5">DLC</subfield>
  </datafield>
  <datafield tag="740" ind1="0" ind2=" ">
    <subfield code="a">Dinosaur dilemna.</subfield>
  </datafield>
  <datafield tag="740" ind1="0" ind2=" ">
    <subfield code="a">Abbott and Costello cartoons.</subfield>
    <subfield code="p">Dinosaur dilemna.</subfield>
  </datafield>
  <datafield tag="953" ind1=" " ind2=" ">
    <subfield code="a">TE01</subfield>
  </datafield>
  <datafield tag="969" ind1=" " ind2=" ">
    <subfield code="a">qxp</subfield>
  </datafield>
  <datafield tag="991" ind1=" " ind2=" ">
    <subfield code="b">c-MP&amp;TV</subfield>
    <subfield code="h">VBK 2042 (viewing copy)</subfield>
    <subfield code="w">MUMS VM File</subfield>
  </datafield>
</record></zs:recordData><zs:recordPosition>4</zs:recordPosition></zs:record><zs:record><zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema><zs:recordPacking>xml</zs:recordPacking><zs:recordData><record xmlns="http://www.loc.gov/MARC21/slim">
  <leader>01461ngm a22003375a 4500</leader>
  <controlfield tag="001">11624468</controlfield>
  <controlfield tag="005">00000000000000.0</controlfield>
  <controlfield tag="008">930921s1967    xxu               vaeng  </controlfield>
  <datafield tag="035" ind1=" " ind2=" ">
    <subfield code="9">(DLC)   93513621</subfield>
  </datafield>
  <datafield tag="906" ind1=" " ind2=" ">
    <subfield code="a">0</subfield>
    <subfield code="b">ibc</subfield>
    <subfield code="c">orignew</subfield>
    <subfield code="d">u</subfield>
    <subfield code="e">ncip</subfield>
    <subfield code="f">19</subfield>
    <subfield code="g">y-movingim</subfield>
  </datafield>
  <datafield tag="010" ind1=" " ind2=" ">
    <subfield code="a">   93513621 </subfield>
  </datafield>
  <controlfield tag="007">v| ||||||</controlfield>
  <datafield tag="017" ind1=" " ind2=" ">
    <subfield code="a">PA608-252</subfield>
    <subfield code="b">U.S. Copyright Office</subfield>
  </datafield>
  <datafield tag="040" ind1=" " ind2=" ">
    <subfield code="a">DLC</subfield>
    <subfield code="c">DLC</subfield>
    <subfield code="e">amim</subfield>
  </datafield>
  <datafield tag="050" ind1="0" ind2="0">
    <subfield code="a">VBK 2042 (viewing copy)</subfield>
  </datafield>
  <datafield tag="245" ind1="0" ind2="0">
    <subfield code="a">Abbott &amp; Costello cartoons.</subfield>
    <subfield code="p">Frigid fugitive /</subfield>
    <subfield code="c">a Hanna-Barbera Production in association with RKO Pictures Company-Jomar Productions ; directed and produced by Joseph Barbera and William Hanna.</subfield>
  </datafield>
  <datafield tag="260" ind1=" " ind2=" ">
    <subfield code="a">United States :</subfield>
    <subfield code="b">[s.n.],</subfield>
    <subfield code="c">1967.</subfield>
  </datafield>
  <datafield tag="300" ind1=" " ind2=" ">
    <subfield code="a">1 videocassette of 1 :</subfield>
    <subfield code="b">sd., col. ;</subfield>
    <subfield code="c">3/4 in. viewing copy.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Copyright: PUB 12May67; PA608-252.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Copyright notice on film: RKO General Inc., Jomar Prod. Inc., Hanna-Barbera Productions, Inc. ; 1967.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">On cassette with episodes: Invader raider ; Dinosaur dilemna ; Paddleboat pirate.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Number 12.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Animation.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Source used: copyright data sheet.</subfield>
  </datafield>
  <datafield tag="541" ind1=" " ind2=" ">
    <subfield code="d">Received: 4/27/1993;</subfield>
    <subfield code="3">viewing copy;</subfield>
    <subfield code="c">copyright deposit--RNR;</subfield>
    <subfield code="a">Copyright Collection.</subfield>
  </datafield>
  <datafield tag="710" ind1="2" ind2=" ">
    <subfield code="a">Copyright Collection (Library of Congress)</subfield>
    <subfield code="5">DLC</subfield>
  </datafield>
  <datafield tag="740" ind1="0" ind2=" ">
    <subfield code="a">Frigid fugitive.</subfield>
  </datafield>
  <datafield tag="740" ind1="0" ind2=" ">
    <subfield code="a">Abbott and Costello cartoons.</subfield>
    <subfield code="p">Frigid fugitive.</subfield>
  </datafield>
  <datafield tag="953" ind1=" " ind2=" ">
    <subfield code="a">TE01</subfield>
  </datafield>
  <datafield tag="969" ind1=" " ind2=" ">
    <subfield code="a">qxp</subfield>
  </datafield>
  <datafield tag="991" ind1=" " ind2=" ">
    <subfield code="b">c-MP&amp;TV</subfield>
    <subfield code="h">VBK 2042 (viewing copy)</subfield>
    <subfield code="w">MUMS VM File</subfield>
  </datafield>
</record></zs:recordData><zs:recordPosition>5</zs:recordPosition></zs:record><zs:record><zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema><zs:recordPacking>xml</zs:recordPacking><zs:recordData><record xmlns="http://www.loc.gov/MARC21/slim">
  <leader>01458ngm a22003375a 4500</leader>
  <controlfield tag="001">11624469</controlfield>
  <controlfield tag="005">00000000000000.0</controlfield>
  <controlfield tag="008">930921s1967    xxu               vaeng  </controlfield>
  <datafield tag="035" ind1=" " ind2=" ">
    <subfield code="9">(DLC)   93513622</subfield>
  </datafield>
  <datafield tag="906" ind1=" " ind2=" ">
    <subfield code="a">0</subfield>
    <subfield code="b">ibc</subfield>
    <subfield code="c">orignew</subfield>
    <subfield code="d">u</subfield>
    <subfield code="e">ncip</subfield>
    <subfield code="f">19</subfield>
    <subfield code="g">y-movingim</subfield>
  </datafield>
  <datafield tag="010" ind1=" " ind2=" ">
    <subfield code="a">   93513622 </subfield>
  </datafield>
  <controlfield tag="007">v| ||||||</controlfield>
  <datafield tag="017" ind1=" " ind2=" ">
    <subfield code="a">PA608-253</subfield>
    <subfield code="b">U.S. Copyright Office</subfield>
  </datafield>
  <datafield tag="040" ind1=" " ind2=" ">
    <subfield code="a">DLC</subfield>
    <subfield code="c">DLC</subfield>
    <subfield code="e">amim</subfield>
  </datafield>
  <datafield tag="050" ind1="0" ind2="0">
    <subfield code="a">VBK 2042 (viewing copy)</subfield>
  </datafield>
  <datafield tag="245" ind1="0" ind2="0">
    <subfield code="a">Abbott &amp; Costello cartoons.</subfield>
    <subfield code="p">Invader raider /</subfield>
    <subfield code="c">a Hanna-Barbera Production in association with RKO Pictures Company-Jomar Productions ; directed and produced by Joseph Barbera and William Hanna.</subfield>
  </datafield>
  <datafield tag="260" ind1=" " ind2=" ">
    <subfield code="a">United States :</subfield>
    <subfield code="b">[s.n.],</subfield>
    <subfield code="c">1967.</subfield>
  </datafield>
  <datafield tag="300" ind1=" " ind2=" ">
    <subfield code="a">1 videocassette of 1 :</subfield>
    <subfield code="b">sd., col. ;</subfield>
    <subfield code="c">3/4 in. viewing copy.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Copyright: PUB 1Jun67; PA608-253.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Copyright notice on film: RKO General Inc., Jomar Prod. Inc., Hanna-Barbera Productions, Inc. ; 1967.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">On cassette with episodes: Frigid fugitive ; Dinosaur dilemna ; Paddleboat pirate.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Number 12.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Animation.</subfield>
  </datafield>
  <datafield tag="500" ind1=" " ind2=" ">
    <subfield code="a">Source used: copyright data sheet.</subfield>
  </datafield>
  <datafield tag="541" ind1=" " ind2=" ">
    <subfield code="d">Received: 4/27/1993;</subfield>
    <subfield code="3">viewing copy;</subfield>
    <subfield code="c">copyright deposit--RNR;</subfield>
    <subfield code="a">Copyright Collection.</subfield>
  </datafield>
  <datafield tag="710" ind1="2" ind2=" ">
    <subfield code="a">Copyright Collection (Library of Congress)</subfield>
    <subfield code="5">DLC</subfield>
  </datafield>
  <datafield tag="740" ind1="0" ind2=" ">
    <subfield code="a">Invader raider.</subfield>
  </datafield>
  <datafield tag="740" ind1="0" ind2=" ">
    <subfield code="a">Abbott and Costello cartoons.</subfield>
    <subfield code="p">Invader raider.</subfield>
  </datafield>
  <datafield tag="953" ind1=" " ind2=" ">
    <subfield code="a">TE01</subfield>
  </datafield>
  <datafield tag="969" ind1=" " ind2=" ">
    <subfield code="a">qxp</subfield>
  </datafield>
  <datafield tag="991" ind1=" " ind2=" ">
    <subfield code="b">c-MP&amp;TV</subfield>
    <subfield code="h">VBK 2042 (viewing copy)</subfield>
    <subfield code="w">MUMS VM File</subfield>
  </datafield>
</record></zs:recordData><zs:recordPosition>6</zs:recordPosition></zs:record></zs:records></zs:searchRetrieveResponse>[/PHP]

---

### Post by sdowney717 on 2011-02-21
still no joy. here trying to load into string.
supposedly it errors, but does not say what the errors are.
do these xml parsing functions even work?
[http://us2.php.net/manual/en/function.libxml-get-errors.php](http://us2.php.net/manual/en/function.libxml-get-errors.php)
[PHP]<?php

libxml_use_internal_errors(true);

$xmlstr = <<< XML
<?xml version='1.0' standalone='yes'?>
<movies>
 <movie>
  <titles>PHP: Behind the Parser</title>
 </movie>
</movies>
XML;

   $request='http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&startRecord=2&maximumRecords=5';
   //echo $request;
 //  $filename = dirname(__FILE__)."/loc.xml";
   $raw_xml = file_get_contents($request);


$doc = simplexml_load_string($raw_xml);
$xml = explode("\n", $raw_xml);
var_dump ($doc);

//print_r ($xml);

if (!$doc) {
    $errors = libxml_get_errors();
    echo 'yes an error';
    foreach ($errors as $error) {
        echo display_xml_error($error, $xml);
    }

    libxml_clear_errors();
}


function display_xml_error($error, $xml)
{
    $return  = $xml[$error->line - 1] . "\n";
    $return .= str_repeat('-', $error->column) . "^\n";
print_r($error);
    switch ($error->level) {
        case LIBXML_ERR_WARNING:
            $return .= "Warning $error->code: ";
            break;
         case LIBXML_ERR_ERROR:
            $return .= "Error $error->code: ";
            break;
        case LIBXML_ERR_FATAL:
            $return .= "Fatal Error $error->code: ";
            break;
    }

    $return .= trim($error->message) .
               "\n  Line: $error->line" .
               "\n  Column: $error->column";

    if ($error->file) {
        $return .= "\n  File: $error->file";
    }

    return "$return\n\n--------------------------------------------\n\n";
}

?>[/PHP]

---

