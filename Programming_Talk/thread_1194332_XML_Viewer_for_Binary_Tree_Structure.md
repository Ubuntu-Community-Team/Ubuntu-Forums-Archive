---
title: "XML Viewer for Binary Tree Structure?"
date: 2009-06-22
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-06-22
I used XMLEncoder in Java to encode a tree structure for debugging my program.  I create a class called Node to represent each node of the tree.  Each node of the tree represents either a function or terminal.  All nodes evaluate to a double or boolean result.  So my node has the following properties:

[PHP]	
	private Node left;
	private Node right;
	private double doubleresult;
	private boolean booleanresult;
	private String nodetype;
[/PHP]

So far, each node can have at most two child nodes.  If a node only has one child, then then it is assigned to the left variable above.  Anyhow, using XMLEncoder on the Node class described above produces XML that looks like this:

[PHP]  
<void index="14"> 
   <object class="Node"> 
    <void property="booleanresult"> 
     <boolean>true</boolean> 
    </void> 
    <void property="left"> 
     <object class="Node"> 
      <void property="booleanresult"> 
       <boolean>true</boolean> 
      </void> 
      <void property="left"> 
       <object class="Node"> 
        <void property="booleanresult"> 
         <boolean>true</boolean> 
        </void> 
        <void property="left"> 
         <object class="Node"> 
          <void property="booleanresult"> 
           <boolean>true</boolean> 
          </void> 
          <void property="left"> 
           <object class="Node"> 
            <void property="booleanresult"> 
             <boolean>true</boolean> 
            </void> 
            <void property="nodetype"> 
             <string>TRUE NODE</string> 
            </void> 
           </object> 
          </void> 
          <void property="nodetype"> 
           <string>AND FUNCTION</string> 
          </void> 
          <void property="right"> 
           <object class="Node"> 
            <void property="booleanresult"> 
             <boolean>true</boolean> 
            </void> 
            <void property="nodetype"> 
             <string>TRUE NODE</string> 
            </void> 
           </object> 
          </void> 
         </object> 
        </void> 
        <void property="nodetype"> 
         <string>AND FUNCTION</string> 
        </void> 
        <void property="right"> 
         <object class="Node"> 
          <void property="booleanresult"> 
           <boolean>true</boolean> 
          </void> 
          <void property="left"> 
           <object class="Node"> 
            <void property="doubleresult"> 
             <double>77.70738772700724</double> 
            </void> 
            <void property="nodetype"> 
             <string>DOUBLE NODE</string> 
            </void> 
           </object> 
          </void> 
          <void property="nodetype"> 
           <string>GREATER THAN FUNCTION</string> 
          </void> 
          <void property="right"> 
           <object class="Node"> 
            <void property="doubleresult"> 
             <double>2.6955063715627094</double> 
            </void> 
            <void property="nodetype"> 
             <string>DOUBLE NODE</string> 
            </void> 
           </object> 
          </void> 
         </object> 
        </void> 
       </object> 
      </void> 
      <void property="nodetype"> 
       <string>AND FUNCTION</string> 
      </void> 
      <void property="right"> 
       <object class="Node"> 
        <void property="left"> 
         <object class="Node"> 
          <void property="booleanresult"> 
           <boolean>true</boolean> 
          </void> 
          <void property="nodetype"> 
           <string>TRUE NODE</string> 
          </void> 
         </object> 
        </void> 
        <void property="nodetype"> 
         <string>NOT FUNCTION</string> 
        </void> 
       </object> 
      </void> 
     </object> 
    </void> 
    <void property="nodetype"> 
     <string>AND FUNCTION</string> 
    </void> 
    <void property="right"> 
     <object class="Node"> 
      <void property="booleanresult"> 
       <boolean>true</boolean> 
      </void> 
      <void property="left"> 
       <object class="Node"> 
        <void property="doubleresult"> 
         <double>109.01119999999999</double> 
        </void> 
        <void property="left"> 
         <object class="Node"> 
          <void property="doubleresult"> 
           <double>97.2062</double> 
          </void> 
          <void property="nodetype"> 
           <string>DOUBLE NODE</string> 
          </void> 
         </object> 
        </void> 
        <void property="nodetype"> 
         <string>SUM FUNCTION</string> 
        </void> 
        <void property="right"> 
         <object class="Node"> 
          <void property="doubleresult"> 
           <double>11.804999999999996</double> 
          </void> 
          <void property="nodetype"> 
           <string>DOUBLE NODE</string> 
          </void> 
         </object> 
        </void> 
       </object> 
      </void> 
      <void property="nodetype"> 
       <string>LESS THAN FUNCTION</string> 
      </void> 
      <void property="right"> 
       <object class="Node"> 
        <void property="doubleresult"> 
         <double>145.65787829340246</double> 
        </void> 
        <void property="left"> 
         <object class="Node"> 
          <void property="doubleresult"> 
           <double>45.588652937204586</double> 
          </void> 
          <void property="left"> 
           <object class="Node"> 
            <void property="doubleresult"> 
             <double>57.39365293720458</double> 
            </void> 
            <void property="nodetype"> 
             <string>DOUBLE NODE</string> 
            </void> 
           </object> 
          </void> 
          <void property="nodetype"> 
           <string>SUBTRACT FUNCTION</string> 
          </void> 
          <void property="right"> 
           <object class="Node"> 
            <void property="doubleresult"> 
             <double>11.804999999999996</double> 
            </void> 
            <void property="nodetype"> 
             <string>DOUBLE NODE</string> 
            </void> 
           </object> 
          </void> 
         </object> 
        </void> 
        <void property="nodetype"> 
         <string>SUM FUNCTION</string> 
        </void> 
        <void property="right"> 
         <object class="Node"> 
          <void property="doubleresult"> 
           <double>100.06922535619789</double> 
          </void> 
          <void property="nodetype"> 
           <string>DOUBLE NODE</string> 
          </void> 
         </object> 
        </void> 
       </object> 
      </void> 
     </object> 
    </void> 
   </object> 
  </void>
[/PHP] 

However, that is only index 14 out of a 2600 length array.  If I only had one tree, I would simply draw it out.  I am looking for some XML viewer which will let me view the tree above.  It would be helpful if each node in the tree could show the value (boolean or double) and the nodetype string.  Does anyone have any suggestions on how I can view the tree?

---

### Post by Reiger on 2009-06-22
Post process it with something like XSLT then save the result and open in any editor which lets you fold XML code blocks.

---

### Post by leblancmeneses on 2009-07-02
if all you need is the tree representation 

**XML Notepad 2007**


[http://www.microsoft.com/downloads/details.aspx?familyid=72d6aa49-787d-4118-ba5f-4f30fe913628&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=72d6aa49-787d-4118-ba5f-4f30fe913628&displaylang=en)

which worked well.


i actually needed this tooo.. and just found this to satisfy my needs.

---

