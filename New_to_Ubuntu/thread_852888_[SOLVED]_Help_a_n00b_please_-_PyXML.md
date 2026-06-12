---
title: "[SOLVED] Help a n00b please - PyXML"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by hayden92 on 2008-07-08
Hello all,

I wasn't sure whether this was the right place for my thread, but here goes...

I have been using the game xmoto for ages and it's really good fun. Recently I installed inkscape so that I could make my own levels. The install went fine and I have the xmoto option in 'Effects'.

The trouble is:
When I either try to convert objects to entities, set object properties, play the level in xmoto I get the following message:

"Inkscape has received additional data from the script executed.  The script did not return an error, but this may indicate the results will not be as expected."
"The inkex.py module requires PyXML. Please download the latest version from <http://pyxml.sourceforge.net/>."

I tried to install PyXML, but I'm not sure where to put the source code really. I tried to compile it by using the commands they suggested on the site e.g: 'python setup.py build' to no avail. I get the message:

extensions/pyexpat.c:512: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer_used&#8217;
extensions/pyexpat.c: In function &#8216;my_StartElementHandler&#8217;:
extensions/pyexpat.c:524: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:524: error: &#8216;container&#8217; undeclared (first use in this function)
extensions/pyexpat.c:524: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:524: warning: left-hand operand of comma expression has no effect
extensions/pyexpat.c:524: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:524: warning: left-hand operand of comma expression has no effect
extensions/pyexpat.c:532: error: &#8216;xmlparseobject&#8217; has no member named &#8216;specified_attributes&#8217;
extensions/pyexpat.c:533: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c:541: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ordered_attributes&#8217;
extensions/pyexpat.c:542: warning: implicit declaration of function &#8216;PyList_New&#8217;
extensions/pyexpat.c:544: warning: implicit declaration of function &#8216;PyDict_New&#8217;
extensions/pyexpat.c:550: error: &#8216;n&#8217; undeclared (first use in this function)
extensions/pyexpat.c:550: warning: implicit declaration of function &#8216;string_intern&#8217;
extensions/pyexpat.c:551: error: &#8216;v&#8217; undeclared (first use in this function)
extensions/pyexpat.c:557: warning: implicit declaration of function &#8216;conv_string_to_utf8&#8217;
extensions/pyexpat.c:564: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ordered_attributes&#8217;
extensions/pyexpat.c:565: warning: implicit declaration of function &#8216;PyList_SET_ITEM&#8217;
extensions/pyexpat.c:568: warning: implicit declaration of function &#8216;PyDict_SetItem&#8217;
extensions/pyexpat.c:579: warning: implicit declaration of function &#8216;Py_BuildValue&#8217;
extensions/pyexpat.c:585: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:587: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:588: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_EndElementHandler&#8217;:
extensions/pyexpat.c:636: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:636: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:636: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:636: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:636: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:636: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_ProcessingInstructionHandler&#8217;:
extensions/pyexpat.c:640: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:640: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:640: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:640: error: &#8216;conv_string_to_utf8&#8217; undeclared (first use in this function)
extensions/pyexpat.c:640: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:640: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:640: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_UnparsedEntityDeclHandler&#8217;:
extensions/pyexpat.c:646: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:646: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:646: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:646: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:646: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:646: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_EntityDeclHandler&#8217;:
extensions/pyexpat.c:659: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:659: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:659: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:659: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:659: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:659: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_XmlDeclHandler&#8217;:
extensions/pyexpat.c:696: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:696: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:696: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:696: error: &#8216;conv_string_to_utf8&#8217; undeclared (first use in this function)
extensions/pyexpat.c:696: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:696: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:696: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:705: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c: In function &#8216;my_ElementDeclHandler&#8217;:
extensions/pyexpat.c:737: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:737: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:740: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:741: error: &#8216;modelobj&#8217; undeclared (first use in this function)
extensions/pyexpat.c:741: error: &#8216;nameobj&#8217; undeclared (first use in this function)
extensions/pyexpat.c:741: warning: left-hand operand of comma expression has no effect
extensions/pyexpat.c:751: warning: implicit declaration of function &#8216;conv_content_model&#8217;
extensions/pyexpat.c:751: error: &#8216;conv_string_to_utf8&#8217; undeclared (first use in this function)
extensions/pyexpat.c:769: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:771: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:772: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:780: warning: implicit declaration of function &#8216;Py_XDECREF&#8217;
extensions/pyexpat.c:781: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c: In function &#8216;my_AttlistDeclHandler&#8217;:
extensions/pyexpat.c:785: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:785: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:785: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:785: error: &#8216;conv_string_to_utf8&#8217; undeclared (first use in this function)
extensions/pyexpat.c:785: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:785: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:785: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_SkippedEntityHandler&#8217;:
extensions/pyexpat.c:798: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:798: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:798: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:798: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:798: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:798: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_NotationDeclHandler&#8217;:
extensions/pyexpat.c:806: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:806: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:806: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:806: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:806: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:806: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_StartNamespaceDeclHandler&#8217;:
extensions/pyexpat.c:816: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:816: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:816: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:816: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:816: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:816: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_EndNamespaceDeclHandler&#8217;:
extensions/pyexpat.c:823: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:823: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:823: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:823: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:823: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:823: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_CommentHandler&#8217;:
extensions/pyexpat.c:828: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:828: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:828: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:828: error: &#8216;conv_string_to_utf8&#8217; undeclared (first use in this function)
extensions/pyexpat.c:828: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:828: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:828: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_StartCdataSectionHandler&#8217;:
extensions/pyexpat.c:832: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:832: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:832: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:832: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:832: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:832: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_EndCdataSectionHandler&#8217;:
extensions/pyexpat.c:836: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:836: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:836: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:836: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:836: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:836: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_DefaultHandler&#8217;:
extensions/pyexpat.c:841: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:841: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:841: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:841: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:841: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:841: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_DefaultHandlerExpandHandler&#8217;:
extensions/pyexpat.c:845: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:845: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:845: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:845: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:845: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:845: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_NotStandaloneHandler&#8217;:
extensions/pyexpat.c:862: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:862: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:862: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:862: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:862: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:862: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:862: warning: implicit declaration of function &#8216;PyInt_AsLong&#8217;
extensions/pyexpat.c: In function &#8216;my_ExternalEntityRefHandler&#8217;:
extensions/pyexpat.c:866: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:866: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:866: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:866: error: &#8216;conv_string_to_utf8&#8217; undeclared (first use in this function)
extensions/pyexpat.c:866: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:866: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:866: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_StartDoctypeDeclHandler&#8217;:
extensions/pyexpat.c:881: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:881: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:881: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:881: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:881: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:881: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: In function &#8216;my_EndDoctypeDeclHandler&#8217;:
extensions/pyexpat.c:889: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:889: error: &#8216;args&#8217; undeclared (first use in this function)
extensions/pyexpat.c:889: error: &#8216;rv&#8217; undeclared (first use in this function)
extensions/pyexpat.c:889: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c:889: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:889: error: &#8216;xmlparseobject&#8217; has no member named &#8216;in_callback&#8217;
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:893: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:912: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:930: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
extensions/pyexpat.c: In function &#8216;readinst&#8217;:
extensions/pyexpat.c:932: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:932: error: &#8216;arg&#8217; undeclared (first use in this function)
extensions/pyexpat.c:933: error: &#8216;bytes&#8217; undeclared (first use in this function)
extensions/pyexpat.c:934: error: &#8216;str&#8217; undeclared (first use in this function)
extensions/pyexpat.c:937: warning: implicit declaration of function &#8216;PyInt_FromLong&#8217;
extensions/pyexpat.c:948: warning: implicit declaration of function &#8216;PyObject_CallObject&#8217;
extensions/pyexpat.c:948: error: &#8216;meth&#8217; undeclared (first use in this function)
extensions/pyexpat.c:956: warning: implicit declaration of function &#8216;PyString_Check&#8217;
extensions/pyexpat.c:957: warning: implicit declaration of function &#8216;PyErr_Format&#8217;
extensions/pyexpat.c:957: error: &#8216;PyExc_TypeError&#8217; undeclared (first use in this function)
extensions/pyexpat.c:962: warning: implicit declaration of function &#8216;PyString_GET_SIZE&#8217;
extensions/pyexpat.c:964: error: &#8216;PyExc_ValueError&#8217; undeclared (first use in this function)
extensions/pyexpat.c:970: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
extensions/pyexpat.c:970: warning: implicit declaration of function &#8216;PyString_AsString&#8217;
extensions/pyexpat.c:970: warning: passing argument 2 of &#8216;memcpy&#8217; makes pointer from integer without a cast
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:981: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1044: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1062: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1077: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1108: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1203: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1223: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1242: error: array type has incomplete element type
extensions/pyexpat.c:1243: error: &#8216;PyCFunction&#8217; undeclared here (not in a function)
extensions/pyexpat.c:1243: error: expected &#8216;}&#8217; before &#8216;xmlparse_Parse&#8217;
extensions/pyexpat.c:1245: error: expected &#8216;}&#8217; before &#8216;xmlparse_ParseFile&#8217;
extensions/pyexpat.c:1247: error: expected &#8216;}&#8217; before &#8216;xmlparse_SetBase&#8217;
extensions/pyexpat.c:1249: error: expected &#8216;}&#8217; before &#8216;xmlparse_GetBase&#8217;
extensions/pyexpat.c:1251: error: expected &#8216;}&#8217; before &#8216;xmlparse_ExternalEntityParserCreate&#8217;
extensions/pyexpat.c:1253: error: expected &#8216;}&#8217; before &#8216;xmlparse_SetParamEntityParsing&#8217;
extensions/pyexpat.c:1255: error: expected &#8216;}&#8217; before &#8216;xmlparse_GetInputContext&#8217;
extensions/pyexpat.c:1258: error: expected &#8216;}&#8217; before &#8216;xmlparse_UseForeignDTD&#8217;
extensions/pyexpat.c:1320: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c: In function &#8216;xmlparse_dealloc&#8217;:
extensions/pyexpat.c:1395: warning: implicit declaration of function &#8216;PyObject_GC_Fini&#8217;
extensions/pyexpat.c:1397: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c:1398: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c:1399: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c:1401: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1402: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1402: error: &#8216;temp&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1404: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1405: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1408: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1409: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1411: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1412: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1413: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1415: error: &#8216;xmlparseobject&#8217; has no member named &#8216;intern&#8217;
extensions/pyexpat.c:1418: warning: implicit declaration of function &#8216;PyObject_Del&#8217;
extensions/pyexpat.c: In function &#8216;handlername2int&#8217;:
extensions/pyexpat.c:1430: warning: implicit declaration of function &#8216;strcmp&#8217;
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:1437: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1445: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1549: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
extensions/pyexpat.c: In function &#8216;sethandler&#8217;:
extensions/pyexpat.c:1554: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1554: error: &#8216;temp&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1554: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1556: error: &#8216;v&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1556: error: &#8216;Py_None&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1559: warning: implicit declaration of function &#8216;Py_INCREF&#8217;
extensions/pyexpat.c:1562: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:1564: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:1571: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
extensions/pyexpat.c: In function &#8216;xmlparse_setattr&#8217;:
extensions/pyexpat.c:1574: error: &#8216;v&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1575: warning: implicit declaration of function &#8216;PyErr_SetString&#8217;
extensions/pyexpat.c:1575: error: &#8216;PyExc_RuntimeError&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1579: warning: implicit declaration of function &#8216;PyObject_IsTrue&#8217;
extensions/pyexpat.c:1580: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1581: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1581: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer_size&#8217;
extensions/pyexpat.c:1582: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1583: warning: implicit declaration of function &#8216;PyErr_NoMemory&#8217;
extensions/pyexpat.c:1586: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer_used&#8217;
extensions/pyexpat.c:1589: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1592: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1593: error: &#8216;xmlparseobject&#8217; has no member named &#8216;buffer&#8217;
extensions/pyexpat.c:1599: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ns_prefixes&#8217;
extensions/pyexpat.c:1601: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ns_prefixes&#8217;
extensions/pyexpat.c:1602: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
extensions/pyexpat.c:1602: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ns_prefixes&#8217;
extensions/pyexpat.c:1607: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ordered_attributes&#8217;
extensions/pyexpat.c:1609: error: &#8216;xmlparseobject&#8217; has no member named &#8216;ordered_attributes&#8217;
extensions/pyexpat.c:1615: error: &#8216;PyExc_ValueError&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1623: error: &#8216;xmlparseobject&#8217; has no member named &#8216;returns_unicode&#8217;
extensions/pyexpat.c:1628: error: &#8216;xmlparseobject&#8217; has no member named &#8216;specified_attributes&#8217;
extensions/pyexpat.c:1630: error: &#8216;xmlparseobject&#8217; has no member named &#8216;specified_attributes&#8217;
extensions/pyexpat.c:1642: error: too many arguments to function &#8216;sethandler&#8217;
extensions/pyexpat.c:1645: error: &#8216;PyExc_AttributeError&#8217; undeclared (first use in this function)
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:1676: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Xmlparsetype&#8217;
extensions/pyexpat.c:1719: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1766: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c:1778: error: array type has incomplete element type
extensions/pyexpat.c:1779: error: expected &#8216;}&#8217; before &#8216;pyexpat_ParserCreate&#8217;
extensions/pyexpat.c:1781: error: expected &#8216;}&#8217; before &#8216;pyexpat_ErrorString&#8217;
extensions/pyexpat.c:1797: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
extensions/pyexpat.c: In function &#8216;initpyexpat&#8217;:
extensions/pyexpat.c:1835: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1835: error: &#8216;m&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1835: error: &#8216;d&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1835: warning: left-hand operand of comma expression has no effect
extensions/pyexpat.c:1836: error: &#8216;errmod_name&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1836: warning: implicit declaration of function &#8216;PyString_FromString&#8217;
extensions/pyexpat.c:1837: error: &#8216;errors_module&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1838: error: &#8216;modelmod_name&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1839: error: &#8216;model_module&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1840: error: &#8216;sys_modules&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1848: error: &#8216;Xmlparsetype&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1848: error: &#8216;PyType_Type&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1851: warning: implicit declaration of function &#8216;Py_InitModule3&#8217;
extensions/pyexpat.c:1855: error: &#8216;ErrorObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1856: warning: implicit declaration of function &#8216;PyErr_NewException&#8217;
extensions/pyexpat.c:1862: warning: implicit declaration of function &#8216;PyModule_AddObject&#8217;
extensions/pyexpat.c:1866: error: expected expression before &#8216;)&#8217; token
extensions/pyexpat.c:1868: warning: implicit declaration of function &#8216;get_version_string&#8217;
extensions/pyexpat.c:1869: warning: implicit declaration of function &#8216;PyModule_AddStringConstant&#8217;
extensions/pyexpat.c:1889: warning: implicit declaration of function &#8216;PySys_GetObject&#8217;
extensions/pyexpat.c:1890: warning: implicit declaration of function &#8216;PyModule_GetDict&#8217;
extensions/pyexpat.c:1891: warning: implicit declaration of function &#8216;PyDict_GetItem&#8217;
extensions/pyexpat.c:1893: warning: implicit declaration of function &#8216;PyModule_New&#8217;
extensions/pyexpat.c:1918: error: &#8216;list&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1921: warning: implicit declaration of function &#8216;PyErr_Clear&#8217;
extensions/pyexpat.c:1926: error: &#8216;item&#8217; undeclared (first use in this function)
extensions/pyexpat.c:1933: warning: implicit declaration of function &#8216;PyList_Append&#8217;
extensions/pyexpat.c:1996: warning: implicit declaration of function &#8216;PyModule_AddIntConstant&#8217;
extensions/pyexpat.c: In function &#8216;clear_handlers&#8217;:
extensions/pyexpat.c:2023: error: &#8216;PyObject&#8217; undeclared (first use in this function)
extensions/pyexpat.c:2023: error: &#8216;temp&#8217; undeclared (first use in this function)
extensions/pyexpat.c:2027: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:2029: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:2030: error: &#8216;xmlparseobject&#8217; has no member named &#8216;handlers&#8217;
extensions/pyexpat.c:2032: error: &#8216;xmlparseobject&#8217; has no member named &#8216;itself&#8217;
error: command 'gcc' failed with exit status 1
hayden@hayden-desktop:~/inksmoto-0.4.1$ 

I don't know whether that helps.
Please, help me out if you can.

(I also included a screenshot, if that helps)

---

### Post by DezSP on 2008-07-08
PyXML is in the repository:

sudo apt-get install python-xml

---

### Post by hayden92 on 2008-07-08
Thanks for the reply, but I installed python-xml when I installed inkscape. When I tried that command again it says, 'python-xml is already the latest version'

Any way to re-install?

EDIT: Tried that using synaptic, it didn't help. Any other suggestions

---

### Post by DezSP on 2008-07-09
Try installing python-lxml and python-numpy. [Some sort of bug](https://bugs.launchpad.net/inkscape/+bug/168744), apparently...

---

### Post by hayden92 on 2008-07-09
Thank you so much! That did the trick.
Xmoto, here I come!

---

