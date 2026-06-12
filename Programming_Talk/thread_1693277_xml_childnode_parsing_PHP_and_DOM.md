---
title: "xml childnode parsing PHP and DOM"
date: 2011-02-22
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-22
I read this xml file, and discovered I need to parse the child nodes called subfields

As this code is currently written it just prints them all out, but it needs to print the subfield child nodes of the datafield associated with the datafield

[PHP]<?php

$doc = new DOMDocument();
$doc->load( 'loc.xml' );

$librecords = $doc->getElementsByTagName( "record" );

foreach( $librecords as $record ){

   $leader = $record->getElementsByTagName( "leader" );
   $controlfields = $record->getElementsByTagName( "controlfield" ); 
   $datafields = $record->getElementsByTagName( "datafield" ); 
   $subfields = $record->getElementsByTagName( "subfield" );

   $leader = $leader->item(0)->nodeValue;  
   echo '=LDR '.$leader.'<BR>';

   foreach( $controlfields as $controlfield ){
      $tag = $controlfield->getAttribute('tag');  
      $cf_value = $controlfield->firstChild->nodeValue;
      echo "=".$tag." ".$cf_value.'<BR>';  }

   foreach( $datafields as $datafield ){
      $tag = $datafield->getAttribute('tag');  
      $ind1 = $datafield->getAttribute('ind1'); 
      $ind2 = $datafield->getAttribute('ind2'); 
      if ($ind1 ==" ") {$ind1 = "_";}
      if ($ind2 ==" ") {$ind2 = "_";}
      echo "=".$tag." ".$ind1.$ind2; 

      if($datafield->hasChildNodes()){echo 'This node has children!<br />';}



      echo '<BR>'; 
      }
    



   foreach( $subfields as $subfield ){
      $code = $subfield->getAttribute('code');  
      $sf_value = $subfield->firstChild->nodeValue;
      echo '$'.$code.$sf_value.'<BR>'; }





echo '<BR><BR>';

}
?>

   [/PHP]

here is the loc.xml file

```
<?xml version="1.0"?>
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
</record></zs:recordData><zs:recordPosition>6</zs:recordPosition></zs:record></zs:records></zs:searchRetrieveResponse>
```

---

### Post by myrtle1908 on 2011-02-22
> **sdowney717 said:**
> As this code is currently written it just prints them all out, but it needs to print the subfield child nodes of the datafield associated with the datafield

So just check if the datafield has children (subfields) and parse them accordingly.  I'm not sure if PHPs DOM impl of getElementsByTagName searches all children recursively so this line ... 

```
$subfields = $record->getElementsByTagName( "subfield" ); 
```

may well be returning 0 elements because subfield are not children of record.

**Later edit: I misread your initial problem, it prints them all out because you are calling getElementsByTagName on the record rather than the datafield ie. calling it on record finds them all ... just do as I've suggested below ...**

So, in this block ...

```

...
foreach ($datafields as $datafield) {
  ...
  if ($datafield->hasChildNodes()) {
     // parse the subfields.
  }
}

```

just check for children and parse them accordingly.

---

### Post by sdowney717 on 2011-02-23
> just check for children and parse them accordingly.

I tried and cant get it.I spent the last 2 days on it and I am seriously stuck.
I have looked all over and seems like so many different ways to open xml and I think I am using DOM so simplexml wont work.


[PHP]<?php
//http://www.phpbuilder.com/columns/DOM-XML-extension/Octavia_Anghel102710.php3
//child nodes http://www.w3schools.com/php/php_xml_dom.asp
//http://books.google.com/books?id=ygQRKDEsLecC&pg=PA196&lpg=PA196&dq=print+php+xml+child+node+attributes&source=bl&ots=TCAhH4kpCt&sig=yJUPXesIkRUrNXdNE9Yr5ul7Wdw&hl=en&ei=U51kTeKQKsL48AbN4MDTBg&sa=X&oi=book_result&ct=result&resnum=10&ved=0CF4Q6AEwCQ#v=onepage&q=print%20php%20xml%20child%20node%20attributes&f=false
//http://stackoverflow.com/questions/4598409/printing-content-of-a-xml-file-using-xml-dom

$doc = new DOMDocument();
$doc->preserveWhiteSpace = FALSE;

$doc->load( 'loc.xml' );
$root = $doc->documentElement;
$type = $root->nodeType;
//print $doc->nodeName."\n";
//print $root->nodeName."\n";
//print $doc->nodeValue."\n";
//print $root->nodeValue."\n";


$librecords = $doc->getElementsByTagName( "record" );

foreach( $librecords as $record ){

   $leader = $record->getElementsByTagName( "leader" );
   $controlfields = $record->getElementsByTagName( "controlfield" ); 
   $datafields = $record->getElementsByTagName( "datafield" ); 
   $subfields = $record->getElementsByTagName( "subfield" );

   $leader = $leader->item(0)->nodeValue;  
   echo '=LDR '.$leader.'<BR>';

   foreach( $controlfields as $controlfield ){
      $tag = $controlfield->getAttribute('tag');  
      $cf_value = $controlfield->firstChild->nodeValue;
      echo "=".$tag." ".$cf_value.'<BR>';  }

   foreach( $datafields as $datafield ){
      $tag = $datafield->getAttribute('tag');  
      $ind1 = $datafield->getAttribute('ind1'); 
      $ind2 = $datafield->getAttribute('ind2'); 
      if ($ind1 ==" ") {$ind1 = "_";}
      if ($ind2 ==" ") {$ind2 = "_";}
      echo "=".$tag." ".$ind1.$ind2; 

      //if($datafield->hasChildNodes()){echo 'This node has children!<br />';}
      foreach ($datafield->childNodes AS $item)  {  
       
      print 'nodeName '.$item->nodeName . " = " . $item->nodeValue." | " ;} //. "<br />";  }
  
  //   foreach ($datafield->children() as $node) {
  //      $arr = $node->attributes();   // returns an array
  //      print ("code=".$arr["code"]);     // get the value of this attribute
 //       print ("  Company=".$node->subfield);
//        print ("<p><hr>");
//}
 //     foreach( $subfields as $subfield){
      
 //     foreach($subfield->attributes as $attr){

     // $attributes = $subfield->attributes;

     
  //      print $attr->nodeName;
    //    print $attr->nodeValue;
   //     //print $attributes->nodeName;
        //print $attributes->nodeValue;

   //    print $subfield->nodeName;
    //   print $subfield->nodeValue;

//}}
    
   // print $item->nodeValue  ;  
 //       print $item->attributes("code");
   //       $valueID = $item->getAttribute('code'); 
   //      print $item->nodeName->attributes("code");
//          echo $item->nodeValue.getAttribute("code");
      //      print $item->getAttribute('code')
//http://www.devshed.com/c/a/PHP/Accessing-Attributes-and-Cloning-Nodes-with-the-DOM-XML-Extension-in-PHP-5/1/
 
      echo '<BR>'; 
     
     }





   foreach( $subfields as $subfield ){
      $code = $subfield->getAttribute('code');  
      $sf_value = $subfield->firstChild->nodeValue;
      echo '$'.$code.$sf_value.'<BR>'; }

echo '<BR>';

}
?>

   [/PHP]

---

### Post by ja660k on 2011-02-23
Unless i've got confused by the question, what you need to do is something like this, 
[PHP]
    // select datafield element
    $datafields = $record->getElementsByTagName("datafield"); 
    
    // loop over each datafield
    foreach($datafields as $d){
        $tag  = $d->getAttribute('tag');
        $ind1 = $d->getAttribute('ind1');
        $ind2 = $d->getAttribute('ind2');
        
        $ind1 = ($ind1 == " ") ? "_" : $ind1;
        $ind2 = ($ind2 == " ") ? "_" : $ind2;
        echo "=".$tag." ".$ind1.$ind2."\n"; // excuse the \n, using CLI
        
        if($d->hasChildNodes()){
            // select its subfields
            $subfields = $d->getElementsByTagName('subfield');

            // loop over them
            foreach($subfields as $s){
                
                $code = $getAttribute('code');
                $value = $s->nodeValue;
            }
        }          
    }
[/PHP]

DOM reads your xml file into this virtual structure, think of it like an array (of sorts)(in simplexml you can access it like an array)

```

datafield[0]
        subfield[0]
        subfield[1]
        subfield[2]
datafield[1]
        subfield[0]
        subfield[1]
        subfield[2]
        subfield[3]
        subfield[4]
        subfield[5]
datafield[2]
...
...
...

```
you need to be in datafield to then access **its subfields** or else it will simply get them all, because you asked them too.
I dont want to get into the DOM vs simplexml arguement, but for reading and processing xml, simplexml is very easy, but a bit limited when it comes to writing elements etc,

if this is a project where the xml is constantly growing, you should consider using SAX approach, because DOM becomes rather slow on **big** files.

i hope it helps :)

---

### Post by sdowney717 on 2011-02-23
Thanks for getting back on this. This will never be a large set of records.

I tried your code and it is not picking up any of the child nodes at all.


[PHP]<?php
//http://www.phpbuilder.com/columns/DOM-XML-extension/Octavia_Anghel102710.php3
//child nodes http://www.w3schools.com/php/php_xml_dom.asp
//http://books.google.com/books?id=ygQRKDEsLecC&pg=PA196&lpg=PA196&dq=print+php+xml+child+node+attributes&source=bl&ots=TCAhH4kpCt&sig=yJUPXesIkRUrNXdNE9Yr5ul7Wdw&hl=en&ei=U51kTeKQKsL48AbN4MDTBg&sa=X&oi=book_result&ct=result&resnum=10&ved=0CF4Q6AEwCQ#v=onepage&q=print%20php%20xml%20child%20node%20attributes&f=false
//http://stackoverflow.com/questions/4598409/printing-content-of-a-xml-file-using-xml-dom
//http://www.php.net/manual/en/book.dom.php
$doc = new DOMDocument();
$doc->preserveWhiteSpace = FALSE;

$doc->load( 'loc.xml' );
$root = $doc->documentElement;
$type = $root->nodeType;
//print $doc->nodeName."\n";
//print $root->nodeName."\n";
//print $doc->nodeValue."\n";
//print $root->nodeValue."\n";


$librecords = $doc->getElementsByTagName( "record" );

foreach( $librecords as $record ){

   $leader = $record->getElementsByTagName( "leader" );
   $controlfields = $record->getElementsByTagName( "controlfield" ); 
   $datafields = $record->getElementsByTagName( "datafield" ); 
   $subfields = $record->getElementsByTagName( "subfield" );

   $leader = $leader->item(0)->nodeValue;  
   echo '=LDR '.$leader.'<BR>';

   foreach( $controlfields as $controlfield ){
      $tag = $controlfield->getAttribute('tag');  
      $cf_value = $controlfield->firstChild->nodeValue;
      echo "=".$tag." ".$cf_value.'<BR>';  }
   
    // loop over each datafield
    foreach($datafields as $d){
        $tag  = $d->getAttribute('tag');
        $ind1 = $d->getAttribute('ind1');
        $ind2 = $d->getAttribute('ind2');
        
        $ind1 = ($ind1 == " ") ? "_" : $ind1;
        $ind2 = ($ind2 == " ") ? "_" : $ind2;
        echo "=".$tag." ".$ind1.$ind2; // excuse the \n, using CLI
   
        if($d->hasChildNodes)
          {
            // select its subfields
            $subfields = $d->getElementsByTagName('subfield');

            // loop over them
            foreach($subfields as $s){
                
                $code = $getAttribute('code');
                $value = $s->nodeValue;
                print $code;
                print $value;
            }
        }          
       echo '<BR>';
    }  
  
      echo '<BR>'; 
     
    // }





  

echo '<BR>';

}
?>


 foreach( $subfields as $subfield ){
      $code = $subfield->getAttribute('code');  
      $sf_value = $subfield->firstChild->nodeValue;
      echo '$'.$code.$sf_value.'<BR>'; }[/PHP]

Ultimately it needs to look like this here

basically datafield contents datafield attributes subfield attributes subfield contents

all on one line, datafield starts and stops each line of data

> =LDR 01026ngm a22002773a 4500
=001 16429180
=005 20100823131409.0
=007 vffcjaho|
=008 100823s2010 xxu060 mleng
=906 __$a0$bcbc$corignew$du$encip$f20$gy-movingim
=955 __$bqm12 2010-08-23
=010 __$a 2010608899
=017 __$aPA0001684303$bU.S. Copyright Office
=040 __$aDLC$cDLC$eamim
=050 00$aVBU 4599 (viewing copy)
=245 00$a30 Rock.$pEmmanuelle goes to Dinosaur Land.
=246 30$aEmmanuelle goes to Dinosaur Land
=246 3_$aThirty rock.
=257 __$pEmmanuelle goes to Dinosaur Land
=260 __$aUnited States.$c2010-05-13.
=300 __$a1 videocassette of 1 (Betacam SP) (60 min.) :$bsd., col. ;$c1/2 in.$3viewing copy.
=500 __$aEpisode no. 4021.
=500 __$aSources used: videocassette container; Copyright catalog online; Copyright description.
=655 _0$aSituation comedies (Television programs)
=655 _0$aFiction television programs.
=710 2_$aCopyright Collection (Library of Congress)$5DLC

---

### Post by sdowney717 on 2011-02-23
Thanks, THIS DOES WORK!
I changed
if($d->hasChildNodes)
to
if(!$d->hasChildNodes)

and this line also
$code = $getAttribute('code');
to
$code = $s->getAttribute('code'); 

can you tell me the logic on that?


[PHP]<?php
//http://www.phpbuilder.com/columns/DOM-XML-extension/Octavia_Anghel102710.php3
//child nodes http://www.w3schools.com/php/php_xml_dom.asp
//http://books.google.com/books?id=ygQRKDEsLecC&pg=PA196&lpg=PA196&dq=print+php+xml+child+node+attributes&source=bl&ots=TCAhH4kpCt&sig=yJUPXesIkRUrNXdNE9Yr5ul7Wdw&hl=en&ei=U51kTeKQKsL48AbN4MDTBg&sa=X&oi=book_result&ct=result&resnum=10&ved=0CF4Q6AEwCQ#v=onepage&q=print%20php%20xml%20child%20node%20attributes&f=false
//http://stackoverflow.com/questions/4598409/printing-content-of-a-xml-file-using-xml-dom
//http://www.php.net/manual/en/book.dom.php
$doc = new DOMDocument();
$doc->preserveWhiteSpace = FALSE;

$doc->load( 'loc.xml' );
$root = $doc->documentElement;
$type = $root->nodeType;
//print $doc->nodeName."\n";
//print $root->nodeName."\n";
//print $doc->nodeValue."\n";
//print $root->nodeValue."\n";


$librecords = $doc->getElementsByTagName( "recordData" ); //changed from "record", since it sees 4 record even though it is zs:record!!!

foreach( $librecords as $record ){

   $leader = $record->getElementsByTagName( "leader" );
   $controlfields = $record->getElementsByTagName( "controlfield" ); 
   $datafields = $record->getElementsByTagName( "datafield" ); 
   //$subfields = $record->getElementsByTagName( "subfield" );

   $leader = $leader->item(0)->nodeValue;  
   echo '=LDR '.$leader.'<BR>';

   foreach( $controlfields as $controlfield ){
      $tag = $controlfield->getAttribute('tag');  
      $cf_value = $controlfield->firstChild->nodeValue;
      echo "=".$tag." ".$cf_value.'<BR>';  }
   
    // loop over each datafield
    foreach($datafields as $d){
        $tag  = $d->getAttribute('tag');
        $ind1 = $d->getAttribute('ind1');
        $ind2 = $d->getAttribute('ind2');
        
        $ind1 = ($ind1 == " ") ? "_" : $ind1;
        $ind2 = ($ind2 == " ") ? "_" : $ind2;
        echo "=".$tag." ".$ind1.$ind2; // excuse the \n, using CLI
   
        if(!$d->hasChildNodes)
          {
            // select its subfields
            $subfields = $d->getElementsByTagName('subfield');

            // loop over them
            foreach($subfields as $s){
                
                $code = $s->getAttribute('code');
                $value = $s->nodeValue;
                print '$'.$code;
                print $value;
            }
        }          
       echo '<BR>';
    }  
  
      echo '<BR>'; 
     
    // }





  

echo '<BR>';

}
?>[/PHP]

---

### Post by sdowney717 on 2011-02-23
finally the output here

I was going to give up completely.
I found a bug in simple xml where it can not load xml from LOC due to ':'
in the element names

I talked about it on php freaks and they seemed to thing it is a bug, so I had to use DOM.
[http://www.phpfreaks.com/forums/php-coding-help/why-does-this-simplexml_load_file-not-work/](http://www.phpfreaks.com/forums/php-coding-help/why-does-this-simplexml_load_file-not-work/)

So anyway I was very discouraged until it got working.

---

### Post by ja660k on 2011-02-23
Yeah your 100% right with the
$code = $s->getAttributes...

that was my fault; i didnt check really what i was doing, i just did a var dump and saw that elements were returning.

cudos on the breakthough :)
programming can be extremely frustrating sometimes...

also, i did not know that simplexml doesnt like xml namespaces
thats good to know :)

im glad i could be of help

---

### Post by sdowney717 on 2011-02-23
yeah they tell you how easy xml and simplexml are, but wait until you run into things like ':', or some other limitations.
[http://devzone.zend.com/node/view/id/651](http://devzone.zend.com/node/view/id/651)
I submitted a bug report to php.net, but they wanted a patch to complete the bug report, and I dont have one. I also emailed their mail list so maybe someone can look into it that can get it fixed. 

Or perhaps it is a feature?

---

### Post by sdowney717 on 2011-02-25
well it is still broken. (I FIXED THAT note at bottom)
If there are 2 records in the xml, It prints out 4 records.

record1
record1
record2
record2

Is it because of this?

> $librecords = $doc->getElementsByTagName( "record" );
foreach( $librecords as $record ){

in the xml, there are 4 instances of "record"
so it loops 4 times for 2 records?

> 
<record xmlns="http://www.loc.gov/MARC21/slim">
some data for record1
</record>

</zs:recordData><zs:recordPosition>1</zs:recordPosition></zs:record><zs:record><zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema><zs:recordPacking>xml</zs:recordPacking><zs:recordData><record xmlns="http://www.loc.gov/MARC21/slim">

<record xmlns="http://www.loc.gov/MARC21/slim">
some data for record2
</record>

etc...


also how do you get to the data
<zs:numberOfRecords>10000</zs:numberOfRecords>

and this
<zs:recordPosition>1</zs:recordPosition>



I found out by experimenting that 
<zs:record> and <record xmlns="http://www.loc.gov/MARC21/slim">
are looked at as "record", so that explains the 4 times looping for 2 records, it sees "record" four times.

So I changed "record" to "recordData" and that got it back to printing 2 records instead of four.

---

### Post by ja660k on 2011-02-25
gee, it would help if your xml document was formatted correctly; i didnt even notice a record tag!

can you please post the code you have so far? and ill have a crack at working it out...

do you have a sample of what the output should look like?

---

### Post by sdowney717 on 2011-02-25
Thanks, I think I got it!
The blasted <zs:elementname> threw me off!, it is used as just 'elementname', not 'zs:elementname'
you drop the zs: and then it all works


My next step is to simply get the record count from the example that returns only the record count as an xml

[http://www.loc.gov/standards/sru/simple.html](http://www.loc.gov/standards/sru/simple.html)
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur)
if you run that url, you will see an xml that comes back with just a count, although, I noticed they send the record count along with the real query like so
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&maximumRecords=1](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&maximumRecords=1)

so do you think I should bother with the first one? I mean just getting the record count?
It now feels somewhat redundant?

What I am doing is querying the LOC with a query, getting back the reocrd count, getting back the data, display it in say blocks of 20 records to the user, with pagination of results. Then the user will click on a record link and then it will display the marc record for just the one record. And download it into the database.

[PHP]<?php

//http://www.phpbuilder.com/columns/DOM-XML-extension/Octavia_Anghel102710.php3
//child nodes http://www.w3schools.com/php/php_xml_dom.asp
//http://books.google.com/books?id=ygQRKDEsLecC&pg=PA196&lpg=PA196&dq=print+php+xml+child+node+attributes&source=bl&ots=TCAhH4kpCt&sig=yJUPXesIkRUrNXdNE9Yr5ul7Wdw&hl=en&ei=U51kTeKQKsL48AbN4MDTBg&sa=X&oi=book_result&ct=result&resnum=10&ved=0CF4Q6AEwCQ#v=onepage&q=print%20php%20xml%20child%20node%20attributes&f=false
//http://stackoverflow.com/questions/4598409/printing-content-of-a-xml-file-using-xml-dom
//http://www.nusphere.com/kb/phpmanual/function.domattribute-value.htm
//http://www.php.net/manual/en/book.dom.php
libxml_use_internal_errors(true);
$filename = dirname(__FILE__)."/loc.xml";
if (file_exists($filename)) {}

$doc = new DOMDocument();
$doc->preserveWhiteSpace = FALSE;

$doc->load( 'loc.xml' );

if (!$doc) {
    echo "Failed loading XML\n";
    foreach(libxml_get_errors() as $error) {
        echo "\t", $error->message;
    }
}

$librecords = $doc->getElementsByTagName( "searchRetrieveResponse" );
foreach( $librecords as $record )
  {  
   $leader = $record->getElementsByTagName( "version" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'version '.$leader.'<BR>';
  }

foreach( $librecords as $record )
  {  
   $leader = $record->getElementsByTagName( "numberOfRecords" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'number of records '.$leader.'<BR>';
  }

foreach( $librecords as $record )
  {  
   $leader = $record->getElementsByTagName( "recordSchema" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'record schema '.$leader.'<BR><BR>';
  }


$librecords = $doc->getElementsByTagName( "recordData" );
foreach( $librecords as $record ){

   $leader = $record->getElementsByTagName( "leader" );
   $leader = $leader->item(0)->nodeValue;  
   echo '=LDR '.$leader.'<BR>';
   $controlfields = $record->getElementsByTagName( "controlfield" ); 
   $datafields = $record->getElementsByTagName( "datafield" ); 
  

 
   foreach( $controlfields as $controlfield ){
      $tag = $controlfield->getAttribute('tag');  
      $cf_value = $controlfield->firstChild->nodeValue;
      echo "=".$tag." ".$cf_value.'<BR>';  }
   
    // loop over each datafield
    foreach($datafields as $d){
        $tag  = $d->getAttribute('tag');
        $ind1 = $d->getAttribute('ind1');
        $ind2 = $d->getAttribute('ind2');
        
        $ind1 = ($ind1 == " ") ? "_" : $ind1;
        $ind2 = ($ind2 == " ") ? "_" : $ind2;
        echo "=".$tag." ".$ind1.$ind2; // excuse the \n, using CLI
   
        if(!$d->hasChildNodes)
          {
            // select its subfields
            $subfields = $d->getElementsByTagName('subfield');

            // loop over them
            foreach($subfields as $s){
                
                $code = $s->getAttribute('code');
                $value = $s->nodeValue;
                print '$'.$code;
                print $value;
            }
        }          
       echo '<BR>';
    }  
  
      echo '<BR>';      
 
echo '<BR>';

}
?>[/PHP]

---

### Post by sdowney717 on 2011-02-25
is there a way to shorten this somehow?
it works but does not need a foreach loop 

> $librecords = $doc->getElementsByTagName( "searchRetrieveResponse" );
foreach( $librecords as $record )
  {  
   $leader = $record->getElementsByTagName( "version" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'version '.$leader.'<BR>';
  } 

this is a copy and paste out of firefox returned results
not a great structural look but you can see it 

> &#8722;
<zs:searchRetrieveResponse>
<zs:version>1.1</zs:version>
<zs:numberOfRecords>2145</zs:numberOfRecords>
&#8722;
<zs:records>
&#8722;
<zs:record>
<zs:recordSchema>info:srw/schema/1/marcxml-v1.1</zs:recordSchema>
<zs:recordPacking>xml</zs:recordPacking>
&#8722;
<zs:recordData>
&#8722;
<record>
<leader>02315cmm a22004577a 4500</leader>
<controlfield tag="001">5003946</controlfield>
<controlfield tag="005">20110223010017.0</controlfield>
<controlfield tag="007">co cga||||||||</controlfield>
<controlfield tag="008">970701s1995    cau    cq  m        eng  </controlfield>
&#8722;
<datafield tag="035" ind1=" " ind2=" ">
<subfield code="a">(DLC)5003946</subfield>
</datafield>
&#8722;
<datafield tag="035" ind1=" " ind2=" ">
<subfield code="a">(DLC)97802583</subfield>
</datafield>
&#8722;
<datafield tag="906" ind1=" " ind2=" ">
<subfield code="a">7</subfield>
<subfield code="b">cbc</subfield>
<subfield code="c">orignew</subfield>
<subfield code="d">u</subfield>
<subfield code="e">ncip</subfield>
<subfield code="f">19</subfield>
<subfield code="g">y-movingim</subfield>
</datafield>
&#8722;
<datafield tag="955" ind1=" " ind2=" ">
&#8722;
<subfield code="a">
vb25 07-01-97; vb22 to jd00/lb00 07-07-97; jd99 (subj) 07-09-97; lb09 07-11-97;
</subfield>
&#8722;
<subfield code="a">
vb30 2002-12-19 added 130 (rev vb02 2002-12-19); qm14 2010-12-17
</subfield>
</datafield>
&#8722;
<datafield tag="010" ind1=" " ind2=" ">
<subfield code="a">   97802583 </subfield>
</datafield>
&#8722;
<datafield tag="017" ind1=" " ind2=" ">
<subfield code="a">PA0000831620</subfield>
<subfield code="b">U.S. Copyright Office</subfield>
</datafield>
&#8722;
<datafield tag="020" ind1=" " ind2=" ">
<subfield code="a">1569972133</subfield>
</datafield>
&#8722;
<datafield tag="024" ind1="1" ind2=" ">
<subfield code="a">9781569972137</subfield>
</datafield>
&#8722;
<datafield tag="035" ind1=" " ind2=" ">
<subfield code="9">(DLC)   97802583</subfield>
</datafield>
&#8722;
<datafield tag="040" ind1=" " ind2=" ">
<subfield code="a">DLC</subfield>
<subfield code="c">DLC</subfield>
<subfield code="d">DLC</subfield>
</datafield>
&#8722;
<datafield tag="050" ind1="0" ind2="0">
<subfield code="a">HAA 0029</subfield>
</datafield>
&#8722;
<datafield tag="082" ind1="1" ind2="0">
<subfield code="a">567.9</subfield>
<subfield code="2">12</subfield>
</datafield>
&#8722;
<datafield tag="130" ind1="0" ind2=" ">
<subfield code="a">Dinosaur adventure 3-D</subfield>
</datafield>
&#8722;
<datafield tag="245" ind1="1" ind2="0">
<subfield code="a">3-D dinosaur adventure.</subfield>
</datafield>
&#8722;
<datafield tag="246" ind1="3" ind2=" ">
<subfield code="a">Three-dimensional dinosaur adventure</subfield>
</datafield>
&#8722;
<datafield tag="256" ind1=" " ind2=" ">
<subfield code="a">Computer data and program.</subfield>
</datafield>
&#8722;
<datafield tag="260" ind1=" " ind2=" ">
<subfield code="a">Glendale, CA :</subfield>
<subfield code="b">Knowledge Adventure,</subfield>
<subfield code="c">c1995.</subfield>
</datafield>
&#8722;
<datafield tag="300" ind1=" " ind2=" ">
<subfield code="a">1 computer laser optical disc ;</subfield>
<subfield code="c">4 3/4 in. +</subfield>
&#8722;
<subfield code="e">
1 user's guide + 1 quick reference guide + 2 pairs of three-dimensional eyeglasses.
</subfield>
</datafield>
&#8722;
<datafield tag="538" ind1=" " ind2=" ">
&#8722;
<subfield code="a">
System requirements for PC: 486SX/25MHz processor or higher; 8MB RAM; Windows 3.1, 3.11, or 95; SVGA 256-color graphics adapter; hard drive with 5MB free space; double-speed CD-ROM drive; MPC-compatible sound card; mouse.
</subfield>
</datafield>
&#8722;
<datafield tag="538" ind1=" " ind2=" ">
&#8722;
<subfield code="a">
System requirements for Macintosh: 68040 or Power PC processor; 8MB RAM; System 7.0 or higher; 256-color graphics capability; thirteen-inch color monitor or larger; hard drive with 4MB free space; double-speed CD-ROM drive.
</subfield>
</datafield>
&#8722;
<datafield tag="500" ind1=" " ind2=" ">
<subfield code="a">Title from disc label.</subfield>
</datafield>
&#8722;
<datafield tag="521" ind1=" " ind2=" ">
<subfield code="a">Ages 5 to 10.</subfield>
</datafield>
&#8722;
<datafield tag="520" ind1=" " ind2=" ">
&#8722;
<subfield code="a">
Employs a dinosaur theme-park setting to introduce users to Triassic, Jurassic, and Cretaceous periods. Features hypertext dinosaur encyclopedia covering 150 million years of paleontology. Includes animated video simulations, three-dimensional dinosaur museum, narration, games, activities, and color illustrations.
</subfield>
</datafield>
&#8722;
<datafield tag="500" ind1=" " ind2=" ">
<subfield code="a">Not viewed.</subfield>
</datafield>
&#8722;
<datafield tag="500" ind1=" " ind2=" ">
<subfield code="a">Source used: Copyright catalog online.</subfield>
</datafield>
&#8722;
<datafield tag="650" ind1=" " ind2="0">
<subfield code="a">Dinosaurs</subfield>
<subfield code="v">Juvenile software.</subfield>
</datafield>
&#8722;
<datafield tag="655" ind1=" " ind2="0">
<subfield code="a">Educational games.</subfield>
</datafield>
&#8722;
<datafield tag="655" ind1=" " ind2="0">
<subfield code="a">Video games.</subfield>
</datafield>
&#8722;
<datafield tag="710" ind1="2" ind2=" ">
<subfield code="a">Knowledge Adventure, Inc.</subfield>
</datafield>
&#8722;
<datafield tag="710" ind1="2" ind2=" ">
<subfield code="a">Copyright Collection (Library of Congress)</subfield>
<subfield code="5">DLC</subfield>
</datafield>
&#8722;
<datafield tag="753" ind1=" " ind2=" ">
<subfield code="a">PC</subfield>
<subfield code="c">Windows 3.1</subfield>
</datafield>
&#8722;
<datafield tag="753" ind1=" " ind2=" ">
<subfield code="a">Macintosh</subfield>
<subfield code="c">System 7.0</subfield>
</datafield>
</record>
</zs:recordData>
<zs:recordPosition>1</zs:recordPosition>
</zs:record>
</zs:records>
</zs:searchRetrieveResponse>

---

### Post by sdowney717 on 2011-02-25
the next hurdle to overcome will be when the 20 something list of records is shown, create a clickable link that will display just that one record.

How do you search thru the XML file to utilize the element
> <zs:recordPosition>2</zs:recordPosition>
that pertains to each record?
so that a user will click the link and the pertinent record will display by itself?
I saw something about 'xpath'?

---

### Post by ja660k on 2011-02-25
yeah this is xpath written all over it (if im not confused)
 
Here's the resource that helped me learn xpath...
[http://www.zvon.org/xxl/XPathTutorial/General/examples.html](http://www.zvon.org/xxl/XPathTutorial/General/examples.html)

and you can never really go wrong with w3schools...
[http://www.w3schools.com/xpath/](http://www.w3schools.com/xpath/)

**wait** ill leave this here just incase im wrong, but how do you mean create a clickable link?
so the page will be parsed again and filtered down more?

or this is just a static link to somewhere else on the page?

---

### Post by sdowney717 on 2011-02-25
> wait ill leave this here just incase im wrong, but how do you mean create a clickable link?
so the page will be parsed again and filtered down more?
yes.

my plan is to have these search pages resemble this search site at the LOC.
[http://www.loc.gov/z3950/](http://www.loc.gov/z3950/)
better direct link here
[http://www.loc.gov/cgi-bin/zgate?ACTION=INIT&FORM_HOST_PORT=/prod/www/data/z3950/locils2.html,z3950.loc.gov,7090&CI=110343](http://www.loc.gov/cgi-bin/zgate?ACTION=INIT&FORM_HOST_PORT=/prod/www/data/z3950/locils2.html,z3950.loc.gov,7090&CI=110343)
when you search it displays an abreviated list.
then you click more on this record
and it takes you to the single record, which a user can also toggle between views.
So, i theorize that it will have to process the returned xml file again and then just display the one desired record.
will that be painfully difficult or not too bad?

(I mean just use the original returned xml from LOC, not get another one)
(just get new ones spanning every 20 records, forward or back when the user clicks a google type numbered pagination)



It would have been nice to just use their existing site and scrape the results off the final search, but that cant work well.
so a web service is the answer.

---

### Post by sdowney717 on 2011-02-25
good info on xml dom namespaces
[http://www.itsalif.info/content/php-5-dom-and-xmlreader-reading-xml-namespace-part-1](http://www.itsalif.info/content/php-5-dom-and-xmlreader-reading-xml-namespace-part-1)

I found I had to have it working on zs:record or I could not get the record number into the list.

this code uses the namespace

> getElementsByTagNameNS

$librecords = $doc->getElementsByTagNameNS('http://www.loc.gov/zing/srw/', 'record');

this code now works reading the record number.
I also found I can simply requery the web  server 
asking for a starting record number and return just one record
SO, I wont need to worry about xpath.
So, I will use the record number in the clickable link and the user will click on it and it will return that one record.

[PHP]<?php
http://www.itsalif.info/content/php-5-dom-and-xmlreader-reading-xml-namespace-part-1
//http://www.phpbuilder.com/columns/DOM-XML-extension/Octavia_Anghel102710.php3
//child nodes http://www.w3schools.com/php/php_xml_dom.asp
//http://books.google.com/books?id=ygQRKDEsLecC&pg=PA196&lpg=PA196&dq=print+php+xml+child+node+attributes&source=bl&ots=TCAhH4kpCt&sig=yJUPXesIkRUrNXdNE9Yr5ul7Wdw&hl=en&ei=U51kTeKQKsL48AbN4MDTBg&sa=X&oi=book_result&ct=result&resnum=10&ved=0CF4Q6AEwCQ#v=onepage&q=print%20php%20xml%20child%20node%20attributes&f=false
//http://stackoverflow.com/questions/4598409/printing-content-of-a-xml-file-using-xml-dom
//http://www.nusphere.com/kb/phpmanual/function.domattribute-value.htm
//http://www.php.net/manual/en/book.dom.php
libxml_use_internal_errors(true);
$filename = dirname(__FILE__)."/loc.xml";
if (file_exists($filename)) {}

$doc = new DOMDocument();
$doc->preserveWhiteSpace = FALSE;

$doc->load( 'loc.xml' );

if (!$doc) {
    echo "Failed loading XML\n";
    foreach(libxml_get_errors() as $error) {
        echo "\t", $error->message;
    }
}

$librecords = $doc->getElementsByTagName( "searchRetrieveResponse" );
foreach( $librecords as $record )

   {
   
   $leader = $record->getElementsByTagName( "version" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'version '.$leader.'<BR>';
  }

foreach( $librecords as $record )
  {  
   $leader = $record->getElementsByTagName( "numberOfRecords" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'number of records '.$leader.'<BR>';
  }

foreach( $librecords as $record )
  {  
   $leader = $record->getElementsByTagName( "recordSchema" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'record schema '.$leader.'<BR><BR>';
  }

//start looping thru the xml records
//$librecords = $doc->getElementsByTagNameNS( "record" ); //zs:record recordData
$librecords = $doc->getElementsByTagNameNS('http://www.loc.gov/zing/srw/', 'record'); //->item(0)->nodeValue,

foreach( $librecords as $record ){

   $leader = $record->getElementsByTagName( "recordPosition" );
   $leader = $leader->item(0)->nodeValue;  
   echo 'record position '.$leader.'<BR>';

   $leader = $record->getElementsByTagName( "leader" );
   $leader = $leader->item(0)->nodeValue;  
   echo '=LDR '.$leader.'<BR>';

   $controlfields = $record->getElementsByTagName( "controlfield" ); 
   $datafields = $record->getElementsByTagName( "datafield" ); 
 
   foreach( $controlfields as $controlfield ){
      $tag = $controlfield->getAttribute('tag');  
      $cf_value = $controlfield->firstChild->nodeValue;
      echo "=".$tag." ".$cf_value.'<BR>';  }
   
    // loop over each datafield
    foreach($datafields as $d){
        $tag  = $d->getAttribute('tag');
        $ind1 = $d->getAttribute('ind1');
        $ind2 = $d->getAttribute('ind2');
        
        $ind1 = ($ind1 == " ") ? "_" : $ind1;
        $ind2 = ($ind2 == " ") ? "_" : $ind2;
        echo "=".$tag." ".$ind1.$ind2; // excuse the \n, using CLI
   
        if(!$d->hasChildNodes)
          {
            // select its subfields
            $subfields = $d->getElementsByTagName('subfield');

            // loop over them
            foreach($subfields as $s){
                
                $code = $s->getAttribute('code');
                $value = $s->nodeValue;
                print '$'.$code;
                print $value;
            }
        }          
       echo '<BR>';
    }    
    echo '<BR>';       
echo '<BR>';

}




?>
[/PHP]

---

