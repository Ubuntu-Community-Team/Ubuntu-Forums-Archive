---
title: "[SOLVED] lxml 2.1 w/ gcc 4.2.3"
date: 2008-07-21
forum: Packaging and Compiling Programs
---

### Post by javagamer on 2008-07-21
Hi,
   I'm trying to compile lxml 2.1 since the version in the repository is way out of date.  I followed the instructions and downloaded easy_install, so now I cd to the right directory, run "sudo easy_install lxml" and everything looks fine for a while.  Then, a ton of errors scroll down the screen and it exits with an error from gcc.
The end of my log is here:
```
src/lxml/lxml.etree.c:113982: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_7_IDDict_itervalues’
src/lxml/lxml.etree.c:113986: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__IDDict’
src/lxml/lxml.etree.c:114040: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__IDDict’
src/lxml/lxml.etree.c:114053: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__IDDict’
src/lxml/lxml.etree.c:114059: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__IDDict’
src/lxml/lxml.etree.c:114080: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__IDDict’
src/lxml/lxml.etree.c:114128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114137: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114143: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114152: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114165: error: array type has incomplete element type
src/lxml/lxml.etree.c:114166: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_8XInclude___call__’
src/lxml/lxml.etree.c:114170: error: array type has incomplete element type
src/lxml/lxml.etree.c:114171: error: ‘__pyx_getprop_4lxml_5etree_8XInclude_error_log’ undeclared here (not in a function)
src/lxml/lxml.etree.c:114175: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XInclude’
src/lxml/lxml.etree.c:114229: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XInclude’
src/lxml/lxml.etree.c:114242: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XInclude’
src/lxml/lxml.etree.c:114248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XInclude’
src/lxml/lxml.etree.c:114269: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XInclude’
src/lxml/lxml.etree.c:114318: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114328: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114334: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114343: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114352: error: array type has incomplete element type
src/lxml/lxml.etree.c:114353: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_12_ExsltRegExp_test’
src/lxml/lxml.etree.c:114354: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_12_ExsltRegExp_match’
src/lxml/lxml.etree.c:114355: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_12_ExsltRegExp_replace’
src/lxml/lxml.etree.c:114359: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__ExsltRegExp’
src/lxml/lxml.etree.c:114413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__ExsltRegExp’
src/lxml/lxml.etree.c:114426: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__ExsltRegExp’
src/lxml/lxml.etree.c:114432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__ExsltRegExp’
src/lxml/lxml.etree.c:114453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__ExsltRegExp’
src/lxml/lxml.etree.c:114502: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114520: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114534: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114567: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114600: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114608: error: array type has incomplete element type
src/lxml/lxml.etree.c:114612: error: array type has incomplete element type
src/lxml/lxml.etree.c:114613: error: ‘__pyx_getprop_4lxml_5etree_12_BaseContext_context_node’ undeclared here (not in a function)
src/lxml/lxml.etree.c:114614: error: ‘__pyx_getprop_4lxml_5etree_12_BaseContext_eval_context’ undeclared here (not in a function)
src/lxml/lxml.etree.c:114618: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__BaseContext’
src/lxml/lxml.etree.c:114672: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__BaseContext’
src/lxml/lxml.etree.c:114685: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__BaseContext’
src/lxml/lxml.etree.c:114691: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__BaseContext’
src/lxml/lxml.etree.c:114712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__BaseContext’
src/lxml/lxml.etree.c:114760: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114772: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114781: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114802: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114823: error: array type has incomplete element type
src/lxml/lxml.etree.c:114824: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_21_ElementUnicodeResult_getparent’
src/lxml/lxml.etree.c:114828: error: array type has incomplete element type
src/lxml/lxml.etree.c:114829: error: expected expression before ‘struct’
src/lxml/lxml.etree.c:114830: error: expected expression before ‘struct’
src/lxml/lxml.etree.c:114831: error: expected expression before ‘struct’
src/lxml/lxml.etree.c:114835: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__ElementUnicodeResult’
src/lxml/lxml.etree.c:114889: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__ElementUnicodeResult’
src/lxml/lxml.etree.c:114902: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__ElementUnicodeResult’
src/lxml/lxml.etree.c:114908: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__ElementUnicodeResult’
src/lxml/lxml.etree.c:114929: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__ElementUnicodeResult’
src/lxml/lxml.etree.c:114978: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:114988: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:114994: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115004: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115014: error: array type has incomplete element type
src/lxml/lxml.etree.c:115018: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__XPathContext’
src/lxml/lxml.etree.c:115072: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__XPathContext’
src/lxml/lxml.etree.c:115085: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__XPathContext’
src/lxml/lxml.etree.c:115091: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__XPathContext’
src/lxml/lxml.etree.c:115112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__XPathContext’
src/lxml/lxml.etree.c:115161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:115172: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115188: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115200: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115212: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:115216: error: array type has incomplete element type
src/lxml/lxml.etree.c:115217: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_19_XPathEvaluatorBase_evaluate’
src/lxml/lxml.etree.c:115221: error: array type has incomplete element type
src/lxml/lxml.etree.c:115222: error: ‘__pyx_getprop_4lxml_5etree_19_XPathEvaluatorBase_error_log’ undeclared here (not in a function)
src/lxml/lxml.etree.c:115226: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__XPathEvaluatorBase’
src/lxml/lxml.etree.c:115280: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__XPathEvaluatorBase’
src/lxml/lxml.etree.c:115293: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__XPathEvaluatorBase’
src/lxml/lxml.etree.c:115299: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__XPathEvaluatorBase’
src/lxml/lxml.etree.c:115320: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__XPathEvaluatorBase’
src/lxml/lxml.etree.c:115369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:115379: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115385: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115395: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115405: error: array type has incomplete element type
src/lxml/lxml.etree.c:115406: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_21XPathElementEvaluator_register_namespace’
src/lxml/lxml.etree.c:115407: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_21XPathElementEvaluator_register_namespaces’
src/lxml/lxml.etree.c:115408: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_21XPathElementEvaluator___call__’
src/lxml/lxml.etree.c:115412: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XPathElementEvaluator’
src/lxml/lxml.etree.c:115466: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XPathElementEvaluator’
src/lxml/lxml.etree.c:115479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XPathElementEvaluator’
src/lxml/lxml.etree.c:115485: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XPathElementEvaluator’
src/lxml/lxml.etree.c:115506: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XPathElementEvaluator’
src/lxml/lxml.etree.c:115555: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:115564: error: array type has incomplete element type
src/lxml/lxml.etree.c:115565: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_22XPathDocumentEvaluator___call__’
src/lxml/lxml.etree.c:115569: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XPathDocumentEvaluator’
src/lxml/lxml.etree.c:115623: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XPathDocumentEvaluator’
src/lxml/lxml.etree.c:115636: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XPathDocumentEvaluator’
src/lxml/lxml.etree.c:115642: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XPathDocumentEvaluator’
src/lxml/lxml.etree.c:115663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XPathDocumentEvaluator’
src/lxml/lxml.etree.c:115712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:115722: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115737: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115747: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:115757: error: array type has incomplete element type
src/lxml/lxml.etree.c:115758: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_5XPath___call__’
src/lxml/lxml.etree.c:115759: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_5XPath___repr__’
src/lxml/lxml.etree.c:115763: error: array type has incomplete element type
src/lxml/lxml.etree.c:115764: error: expected expression before ‘struct’
src/lxml/lxml.etree.c:115768: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XPath’
src/lxml/lxml.etree.c:115822: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XPath’
src/lxml/lxml.etree.c:115835: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XPath’
src/lxml/lxml.etree.c:115841: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XPath’
src/lxml/lxml.etree.c:115862: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XPath’
src/lxml/lxml.etree.c:115911: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:115920: error: array type has incomplete element type
src/lxml/lxml.etree.c:115924: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_ETXPath’
src/lxml/lxml.etree.c:115978: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_ETXPath’
src/lxml/lxml.etree.c:115991: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_ETXPath’
src/lxml/lxml.etree.c:115997: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_ETXPath’
src/lxml/lxml.etree.c:116018: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_ETXPath’
src/lxml/lxml.etree.c:116067: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116077: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116083: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116093: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116103: error: array type has incomplete element type
src/lxml/lxml.etree.c:116107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__XSLTResolverContext’
src/lxml/lxml.etree.c:116161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__XSLTResolverContext’
src/lxml/lxml.etree.c:116174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__XSLTResolverContext’
src/lxml/lxml.etree.c:116180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__XSLTResolverContext’
src/lxml/lxml.etree.c:116201: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__XSLTResolverContext’
src/lxml/lxml.etree.c:116250: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116259: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116272: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116276: error: array type has incomplete element type
src/lxml/lxml.etree.c:116277: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_17XSLTAccessControl___repr__’
src/lxml/lxml.etree.c:116281: error: array type has incomplete element type
src/lxml/lxml.etree.c:116282: error: ‘__pyx_getprop_4lxml_5etree_17XSLTAccessControl_options’ undeclared here (not in a function)
src/lxml/lxml.etree.c:116286: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XSLTAccessControl’
src/lxml/lxml.etree.c:116340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XSLTAccessControl’
src/lxml/lxml.etree.c:116353: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XSLTAccessControl’
src/lxml/lxml.etree.c:116359: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XSLTAccessControl’
src/lxml/lxml.etree.c:116380: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XSLTAccessControl’
src/lxml/lxml.etree.c:116429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116440: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116447: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116460: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116473: error: array type has incomplete element type
src/lxml/lxml.etree.c:116477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__XSLTContext’
src/lxml/lxml.etree.c:116531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__XSLTContext’
src/lxml/lxml.etree.c:116544: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__XSLTContext’
src/lxml/lxml.etree.c:116550: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__XSLTContext’
src/lxml/lxml.etree.c:116571: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__XSLTContext’
src/lxml/lxml.etree.c:116620: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116633: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116651: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116669: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116687: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116691: error: array type has incomplete element type
src/lxml/lxml.etree.c:116692: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_4XSLT_apply’
src/lxml/lxml.etree.c:116693: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_4XSLT_tostring’
src/lxml/lxml.etree.c:116694: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_4XSLT___deepcopy__’
src/lxml/lxml.etree.c:116695: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_4XSLT___copy__’
src/lxml/lxml.etree.c:116696: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_4XSLT___call__’
src/lxml/lxml.etree.c:116700: error: array type has incomplete element type
src/lxml/lxml.etree.c:116701: error: ‘__pyx_getprop_4lxml_5etree_4XSLT_error_log’ undeclared here (not in a function)
src/lxml/lxml.etree.c:116705: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XSLT’
src/lxml/lxml.etree.c:116759: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XSLT’
src/lxml/lxml.etree.c:116772: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XSLT’
src/lxml/lxml.etree.c:116778: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XSLT’
src/lxml/lxml.etree.c:116799: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XSLT’
src/lxml/lxml.etree.c:116848: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116859: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116866: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116879: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116892: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:116896: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:116906: error: array type has incomplete element type
src/lxml/lxml.etree.c:116907: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_15_XSLTResultTree___str__’
src/lxml/lxml.etree.c:116908: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_15_XSLTResultTree___unicode__’
src/lxml/lxml.etree.c:116912: error: array type has incomplete element type
src/lxml/lxml.etree.c:116913: error: ‘__pyx_getprop_4lxml_5etree_15_XSLTResultTree_xslt_profile’ undeclared here (not in a function)
src/lxml/lxml.etree.c:116913: error: ‘__pyx_setprop_4lxml_5etree_15_XSLTResultTree_xslt_profile’ undeclared here (not in a function)
src/lxml/lxml.etree.c:116917: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__XSLTResultTree’
src/lxml/lxml.etree.c:116971: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__XSLTResultTree’
src/lxml/lxml.etree.c:116984: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__XSLTResultTree’
src/lxml/lxml.etree.c:116990: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__XSLTResultTree’
src/lxml/lxml.etree.c:117011: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__XSLTResultTree’
src/lxml/lxml.etree.c:117060: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:117069: error: array type has incomplete element type
src/lxml/lxml.etree.c:117070: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_26_XSLTProcessingInstruction_parseXSL’
src/lxml/lxml.etree.c:117071: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_26_XSLTProcessingInstruction_set’
src/lxml/lxml.etree.c:117072: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_26_XSLTProcessingInstruction_get’
src/lxml/lxml.etree.c:117076: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number__XSLTProcessingInstruction’
src/lxml/lxml.etree.c:117130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence__XSLTProcessingInstruction’
src/lxml/lxml.etree.c:117143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping__XSLTProcessingInstruction’
src/lxml/lxml.etree.c:117149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer__XSLTProcessingInstruction’
src/lxml/lxml.etree.c:117170: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree__XSLTProcessingInstruction’
src/lxml/lxml.etree.c:117218: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:117224: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:117228: error: array type has incomplete element type
src/lxml/lxml.etree.c:117229: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_13XSLTExtension_execute’
src/lxml/lxml.etree.c:117230: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_13XSLTExtension_apply_templates’
src/lxml/lxml.etree.c:117234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_XSLTExtension’
src/lxml/lxml.etree.c:117288: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_XSLTExtension’
src/lxml/lxml.etree.c:117301: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_XSLTExtension’
src/lxml/lxml.etree.c:117307: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_XSLTExtension’
src/lxml/lxml.etree.c:117328: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_XSLTExtension’
src/lxml/lxml.etree.c:117376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:117382: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:117395: error: array type has incomplete element type
src/lxml/lxml.etree.c:117396: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_3DTD___call__’
src/lxml/lxml.etree.c:117400: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_DTD’
src/lxml/lxml.etree.c:117454: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_DTD’
src/lxml/lxml.etree.c:117467: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_DTD’
src/lxml/lxml.etree.c:117473: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_DTD’
src/lxml/lxml.etree.c:117494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_DTD’
src/lxml/lxml.etree.c:117542: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:117548: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:117561: error: array type has incomplete element type
src/lxml/lxml.etree.c:117562: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_7RelaxNG___call__’
src/lxml/lxml.etree.c:117566: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_RelaxNG’
src/lxml/lxml.etree.c:117620: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_RelaxNG’
src/lxml/lxml.etree.c:117633: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_RelaxNG’
src/lxml/lxml.etree.c:117639: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_RelaxNG’
src/lxml/lxml.etree.c:117660: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_RelaxNG’
src/lxml/lxml.etree.c:117708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:117714: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:117727: error: array type has incomplete element type
src/lxml/lxml.etree.c:117728: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_10Schematron___call__’
src/lxml/lxml.etree.c:117732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_Schematron’
src/lxml/lxml.etree.c:117786: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_Schematron’
src/lxml/lxml.etree.c:117799: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_Schematron’
src/lxml/lxml.etree.c:117805: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_Schematron’
src/lxml/lxml.etree.c:117826: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_4lxml_5etree_Schematron’
src/lxml/lxml.etree.c:117874: error: array type has incomplete element type
src/lxml/lxml.etree.c:117875: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_Element’
src/lxml/lxml.etree.c:117876: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_Comment’
src/lxml/lxml.etree.c:117877: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_ProcessingInstruction’
src/lxml/lxml.etree.c:117878: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_Entity’
src/lxml/lxml.etree.c:117879: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_SubElement’
src/lxml/lxml.etree.c:117880: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_ElementTree’
src/lxml/lxml.etree.c:117881: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_HTML’
src/lxml/lxml.etree.c:117882: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_XML’
src/lxml/lxml.etree.c:117883: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_fromstring’
src/lxml/lxml.etree.c:117884: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_fromstringlist’
src/lxml/lxml.etree.c:117885: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_iselement’
src/lxml/lxml.etree.c:117886: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_dump’
src/lxml/lxml.etree.c:117887: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_tostring’
src/lxml/lxml.etree.c:117888: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_tostringlist’
src/lxml/lxml.etree.c:117889: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_tounicode’
src/lxml/lxml.etree.c:117890: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_parse’
src/lxml/lxml.etree.c:117891: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_cleanup_namespaces’
src/lxml/lxml.etree.c:117892: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_clear_error_log’
src/lxml/lxml.etree.c:117893: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_use_global_python_log’
src/lxml/lxml.etree.c:117894: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_set_element_class_lookup’
src/lxml/lxml.etree.c:117895: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_FunctionNamespace’
src/lxml/lxml.etree.c:117896: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_set_default_parser’
src/lxml/lxml.etree.c:117897: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_get_default_parser’
src/lxml/lxml.etree.c:117898: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_XMLID’
src/lxml/lxml.etree.c:117899: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_XMLDTDID’
src/lxml/lxml.etree.c:117900: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_parseid’
src/lxml/lxml.etree.c:117901: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_Extension’
src/lxml/lxml.etree.c:117902: error: expected ‘}’ before ‘__pyx_pf_4lxml_5etree_XPathEvaluator’
src/lxml/lxml.etree.c:117923: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initetree’
src/lxml/lxml.etree.c:117924: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initetree’
src/lxml/lxml.etree.c: In function ‘__Pyx_RaiseArgtupleTooLong’:
src/lxml/lxml.etree.c:121214: error: ‘PyExc_TypeError’ undeclared (first use in this function)
src/lxml/lxml.etree.c: At top level:
src/lxml/lxml.etree.c:121218: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121248: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121267: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121326: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121410: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121465: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121473: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121539: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c: In function ‘__Pyx_WriteUnraisable’:
src/lxml/lxml.etree.c:121552: error: ‘PyObject’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121552: error: ‘old_exc’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121552: error: invalid operands to binary *
src/lxml/lxml.etree.c:121552: error: ‘old_val’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121552: error: ‘old_tb’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121553: error: ‘ctx’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121553: error: invalid operands to binary *
src/lxml/lxml.etree.c:121562: error: ‘Py_None’ undeclared (first use in this function)
src/lxml/lxml.etree.c: At top level:
src/lxml/lxml.etree.c:121566: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121581: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121594: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121659: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c: In function ‘__Pyx_InitStrings’:
src/lxml/lxml.etree.c:121675: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
src/lxml/lxml.etree.c:121677: error: ‘__Pyx_StringTabEntry’ has no member named ‘is_unicode’
src/lxml/lxml.etree.c:121677: error: ‘__Pyx_StringTabEntry’ has no member named ‘is_identifier’
src/lxml/lxml.etree.c:121678: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
src/lxml/lxml.etree.c:121678: error: ‘__Pyx_StringTabEntry’ has no member named ‘s’
src/lxml/lxml.etree.c:121678: error: ‘__Pyx_StringTabEntry’ has no member named ‘n’
src/lxml/lxml.etree.c:121679: error: ‘__Pyx_StringTabEntry’ has no member named ‘intern’
src/lxml/lxml.etree.c:121680: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
src/lxml/lxml.etree.c:121680: error: ‘__Pyx_StringTabEntry’ has no member named ‘s’
src/lxml/lxml.etree.c:121682: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
src/lxml/lxml.etree.c:121682: error: ‘__Pyx_StringTabEntry’ has no member named ‘s’
src/lxml/lxml.etree.c:121682: error: ‘__Pyx_StringTabEntry’ has no member named ‘n’
src/lxml/lxml.etree.c:121693: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
src/lxml/lxml.etree.c: In function ‘__Pyx_ExportFunction’:
src/lxml/lxml.etree.c:121701: error: ‘PyObject’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121701: error: ‘d’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121701: error: invalid operands to binary *
src/lxml/lxml.etree.c:121702: error: ‘p’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121702: error: invalid operands to binary *
src/lxml/lxml.etree.c:121703: error: ‘__pyx_m’ undeclared (first use in this function)
src/lxml/lxml.etree.c: At top level:
src/lxml/lxml.etree.c:121726: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121747: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121790: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/lxml/lxml.etree.c:121810:21: error: compile.h: No such file or directory
src/lxml/lxml.etree.c:121811:25: error: frameobject.h: No such file or directory
src/lxml/lxml.etree.c:121812:23: error: traceback.h: No such file or directory
src/lxml/lxml.etree.c: In function ‘__Pyx_AddTraceback’:
src/lxml/lxml.etree.c:121815: error: ‘PyObject’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121815: error: ‘py_srcfile’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121815: error: invalid operands to binary *
src/lxml/lxml.etree.c:121816: error: ‘py_funcname’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121816: error: invalid operands to binary *
src/lxml/lxml.etree.c:121817: error: ‘py_globals’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121817: error: invalid operands to binary *
src/lxml/lxml.etree.c:121818: error: ‘empty_string’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121818: error: invalid operands to binary *
src/lxml/lxml.etree.c:121819: error: ‘PyCodeObject’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121819: error: ‘py_code’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121819: error: invalid operands to binary *
src/lxml/lxml.etree.c:121820: error: ‘PyFrameObject’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121820: error: ‘py_frame’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121820: error: invalid operands to binary *
src/lxml/lxml.etree.c:121843: error: ‘__pyx_m’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121860: error: ‘__pyx_empty_tuple’ undeclared (first use in this function)
src/lxml/lxml.etree.c:121878: error: request for member ‘f_lineno’ in something not a structure or union
src/lxml/lxml.etree.c: At top level:
src/lxml/lxml.etree.c:121890: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121899: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121905: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_PyInt_AsLongLong’
src/lxml/lxml.etree.c:121921: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_PyInt_AsUnsignedLongLong’
src/lxml/lxml.etree.c:121943: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121958: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121973: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:121988: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122003: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122018: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122033: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122048: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122063: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122078: error: expected ‘)’ before ‘*’ token
src/lxml/lxml.etree.c:122093: error: expected ‘)’ before ‘*’ token
error: command 'gcc' failed with exit status 1
javagamer@javagamer-desktop:~/Apps/lxml-2.1$ gcc --version
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

javagamer@javagamer-desktop:~/Apps/lxml-2.1$ 

```
I believe this may be related to my version of gcc, but if that is the case then what should I do?  lxml is very important for a project I'm currently working on and any help would be greatly appreciated.

---

### Post by javagamer on 2008-07-24
*bump*
Is anyone else able to use lxml 2.1 or later?  Can someone who can compile it send me a Hardy AMD64 binary?

---

### Post by javagamer on 2008-07-24
*double bump*
It seems more and more like I'm missing something, but I have libxml2, libxml2-dev, libxslt1.1, and libxslt1-dev installed.  Is there anything I'm missing?  Please help.

---

### Post by javagamer on 2008-07-25
I just needed the python-dev package.  *smacks head*

---

### Post by many_miles on 2008-07-28
javagamer, 

I was having a problem install the perl module XML::LibXML and your post encouraged me to try installing libxml-dev.

After that, I was able to complete the module install via CPAN.

Thanks.

---

### Post by tsmets on 2009-12-13
CPython is 2.5 
+ the packages requested in [installation page]("http://codespeak.net/lxml/installation.html")

```
sudo easy_install lxml
```
returns errors : 
```

tsmets@ubuntu:~/Documents/python/test/xml$ sudo easy_install lxml
sudo: unable to resolve host ubuntu
Searching for lxml
Reading http://pypi.python.org/simple/lxml/
Reading http://codespeak.net/lxml
Best match: lxml 2.2.4
Downloading http://codespeak.net/lxml/lxml-2.2.4.tgz
Processing lxml-2.2.4.tgz
Running lxml-2.2.4/setup.py -q bdist_egg --dist-dir /tmp/easy_install-awbpLh/lxml-2.2.4/egg-dist-tmp-VsEd6q
Building lxml version 2.2.4.
NOTE: Trying to build without Cython, pre-generated 'src/lxml/lxml.etree.c' needs to be available.
ERROR: /bin/sh: xslt-config: not found

** make sure the development packages of libxml2 and libxslt are installed **

Using build configuration of libxslt 
In file included from src/lxml/lxml.etree.c:139:
src/lxml/etree_defs.h:9:31: error: libxml/xmlversion.h: No such file or directory
src/lxml/etree_defs.h:11:4: error: #error the development package of libxml2 (header files etc.) is not installed correctly
src/lxml/etree_defs.h:13:32: error: libxslt/xsltconfig.h: No such file or directory
src/lxml/etree_defs.h:15:4: error: #error the development package of libxslt (header files etc.) is not installed correctly

...

src/lxml/lxml.etree.c:142325: error: &#8216;XML_XPATH_INVALID_CTXT_POSITION&#8217; undeclared (first use in this function)
src/lxml/lxml.etree.c:142663: error: &#8216;LIBXSLT_VERSION&#8217; undeclared (first use in this function)
src/lxml/lxml.etree.c:142675: error: &#8216;xsltLibxsltVersion&#8217; undeclared (first use in this function)
src/lxml/lxml.etree.c:142687: error: &#8216;__pyx_v_4lxml_5etree_XSLT_DOC_DEFAULT_LOADER&#8217; undeclared (first use in this function)
src/lxml/lxml.etree.c:142687: error: &#8216;xsltDocDefaultLoader&#8217; undeclared (first use in this function)
src/lxml/lxml.etree.c:142696: error: &#8216;__pyx_f_4lxml_5etree__xslt_doc_loader&#8217; undeclared (first use in this function)
error: Setup script exited with error: command 'gcc' failed with exit status 1

```

Any help is appreciated

I you look at : 
[http://tightwadtechnica.com/?page_id=4163]("http://tightwadtechnica.com/?page_id=4163")
I did :
```

tsmets@ubuntu:~/Documents/python/test/xml$ sudo apt-get install libxml2-dev libxslt-dev  python-dev  python-setuptools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxslt-dev is a virtual package provided by:
  libxslt1-dev 1.1.22-1ubuntu1.2
You should explicitly select one to install.
E: Package libxslt-dev has no installation candidate
```

I managed to install the missing package : libxslt-dev 
via the GUI and now it seems working




\T,

---

### Post by mnemonik on 2010-01-31
Thanks! This just saved my life!

---

### Post by nourathar on 2010-07-13
thanks ! you saved me a lot of time by posting this...

---

