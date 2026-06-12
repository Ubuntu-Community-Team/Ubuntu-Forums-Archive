---
title: "Online Test Using XML, and Ajax."
date: 2007-05-18
forum: Programming Talk
---

### Post by dyous87 on 2007-05-18
Ok guys so I'm trying to program a web test using some ajax and xml. What I have basically is an xml document with different page content. The content is either text to be read or questions with a list of answers one being the correct one.  I'm trying to get a web page to read the xml document and load the page content one at a time. Basically when you start the test I want it to select "Page 1" and then I want the next page to be "Page 2"

Here is my xml files:

```
<?xml version="1.0" encoding="UTF-8"?>
<pages>

<pageTable>
<page pageID="1"> Page 1 </page>
<content type="text"> 
Fordham University is a private, coeducational research university in the United States, with three residential campuses located in and around New York City. Though now officially an independent institution in the Jesuit tradition, it was originally founded by the Catholic Diocese of New York in 1841 as St. John's College. Fordham is currently one of 28 member institutions in the Association of Jesuit Colleges and Universities. [From Wikipedia: Fordham University]


Click Next to Continue. 
</content>
<nextPage pageID="2"> Next Page </nextPage>
</pageTable>

<pageTable>
<page pageID="2"> Page 2 </page>
<content type="question"> What year was Fordham University founded? </content>
<answer answerID="0"> 1912 </answer>
<answer answerID="1"> 1841 </answer>
<answer answerID="0"> 1801 </answer>
<answer answerID="0"> 1943 </answer>
<nextPage pageID="3"> Submit </nextPage>
</pageTable>

<pageTable>
<page pageID="3"> Page 3 </page>
<content type="text"> You have reached the end of the sample quiz. Thank you! </content>
<nextPage pageID="1"> Back Home </nextPage>
</pageTable>

</pages>
```I successfully got the html page to load the xml document using XMLHTTPRequest  but i can't get it to display anything but the first content page. I want it to have a next page button that would then make it go to the next page and list the answers for the questions in radio buttons. This is my javascript code:

```
<script language="javascript">
  function getData()
  {
    var mozillaFlag = false;
    var XMLHttpRequestObject = false;

    if (window.XMLHttpRequest) {
      XMLHttpRequestObject = new XMLHttpRequest();
      mozillaFlag = true;
    } else if (window.ActiveXObject) {
      XMLHttpRequestObject = new
    ActiveXObject("Microsoft.XMLHTTP");
    }
   
    if(XMLHttpRequestObject) {
      XMLHttpRequestObject.open("GET", "pageTable.xml", true);

      XMLHttpRequestObject.onreadystatechange = function()
      {
    if (XMLHttpRequestObject.readyState == 4 &&
      XMLHttpRequestObject.status == 200) {
      var xmlDocument = XMLHttpRequestObject.responseXML;
      if (mozillaFlag){
         removeWhitespace(xmlDocument);
          }
      displayPageContent(xmlDocument);
      displayNextButton(xmlDocument);
      }
    }
        XMLHttpRequestObject.send(null);
    }
  }
  function displayPageContent (xmldoc)
  {
    var pagesNode, pageTableNode;
    var contentNode, displayText;

    pagesNode = xmldoc.documentElement;
    pageTableNode = pagesNode.firstChild;
    contentNode = pageTableNode.firstChild.nextSibling;

    displayText = contentNode.firstChild.nodeValue;

   var target = document.getElementById("targetDiv");
   target.innerHTML=displayText;
  }

  function displayNextButton (xmldoc)
  {
    var pagesNode, pageTableNode;
    var nextPageNode; displayButton;
    varcontentNode;

    pagesNode = xmldoc.documentElement;
    pageTableNode = pagesNode.firstChild;
    nextPageNode = pageTableNode.lastSibling;
    contentNode = pageTableNode.firstChild.nextSibling;

    displayButton = nextPageNode.firstChild.nodeValue;
    

 
   var target = document.getElementById("targetDiv");
    target.innerHTML=displayButton;
    onclick.displayButton = nextPageContent;
  }

   fucntion nextPageContent (xmldoc)
   {
    var pagesNode, pageTableNode;
    varcontenNode; displayNextPageContent;

    pagesNode = xmldoc.documentElement;
    pageTableNode = pagesNode.firstChild;
    contentNode = pageTableNode.firstChild.nextSibling;

    displayNextPageContent = contentNode.nodeVale + "1";
}

   function removeWhitespace(xml) 
      {
        var loopIndex;

        for (loopIndex = 0; loopIndex < xml.childNodes.length; 
          loopIndex++) {

          var currentNode = xml.childNodes[loopIndex];

          if (currentNode.nodeType == 1) {
            removeWhitespace(currentNode);
          }

          if (((/^\s+$/.test(currentNode.nodeValue))) &&   
            (currentNode.nodeType == 3)) {
              xml.removeChild(xml.childNodes[loopIndex--]);
          }
        }
      }
</script>      
```I would really appreciate it if anyone would be able to let me know how to fix that and what to add to get this working. 

Thanks a lot,

David

---

### Post by ahvargas on 2007-06-22
mmm . You can use a library to do the work for you. Try spry

[http://labs.adobe.com/technologies/spry/](http://labs.adobe.com/technologies/spry/)

I think Spry.XMLDataSet can do the job for you

---

