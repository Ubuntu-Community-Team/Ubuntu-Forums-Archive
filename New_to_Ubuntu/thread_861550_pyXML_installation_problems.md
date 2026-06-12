---
title: "pyXML installation problems"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by watupgroupie on 2008-07-16
I want to make lvl's for xmoto with inksmoto and it require pyXML for some scripts to run. I have everything installed correctly and made my lvl but when I try to convert anything into an xmoto object I get a error: ```
The inkex.py module requires PyXML. Please download the latest version from <http://pyxml.sourceforge.net/>.
```
Okay, so I went into synaptic and found python XML and installed it. Still doesn't work... I go to the site to download pyXML, follow the instructions for install and it still doesn't work. Anyone know what the problem is? During install of pyXML I'm also getting these errors:
```
extensions/pyexpat.c:1274: warning: initialization from incompatible pointer type
extensions/pyexpat.c:1274: error: initializer element is not constant
extensions/pyexpat.c: In function ‘PyUnknownEncodingHandler’:
extensions/pyexpat.c:1291: warning: initialization from incompatible pointer type
extensions/pyexpat.c:1297: warning: passing argument 2 of ‘PyUnicodeUCS4_Decode’ makes pointer from integer without a cast
extensions/pyexpat.c:1299: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1311: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1312: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1314: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1314: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1314: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1314: warning: statement with no effect
extensions/pyexpat.c: In function ‘newxmlparseobject’:
extensions/pyexpat.c:1332: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1333: warning: return from incompatible pointer type
extensions/pyexpat.c:1341: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1348: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1349: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1356: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1356: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1356: error: lvalue required as increment operand
extensions/pyexpat.c:1356: warning: statement with no effect
extensions/pyexpat.c:1362: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1365: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1365: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1365: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1365: warning: statement with no effect
extensions/pyexpat.c:1366: warning: return from incompatible pointer type
extensions/pyexpat.c:1374: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1377: warning: incompatible implicit declaration of built-in function ‘malloc’
extensions/pyexpat.c:1379: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1379: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1379: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1379: warning: statement with no effect
extensions/pyexpat.c: In function ‘xmlparse_dealloc’:
extensions/pyexpat.c:1397: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1399: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1401: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1403: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1405: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1406: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1406: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1406: error: lvalue required as decrement operand
extensions/pyexpat.c:1406: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1406: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1406: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1406: warning: statement with no effect
extensions/pyexpat.c:1408: warning: implicit declaration of function ‘free’
extensions/pyexpat.c:1409: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1411: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1413: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1415: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1415: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1415: error: lvalue required as decrement operand
extensions/pyexpat.c:1415: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1415: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1415: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1415: warning: statement with no effect
extensions/pyexpat.c: In function ‘handlername2int’:
extensions/pyexpat.c:1429: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1430: warning: implicit declaration of function ‘strcmp’
extensions/pyexpat.c: In function ‘get_pybool’:
extensions/pyexpat.c:1441: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1441: error: lvalue required as increment operand
extensions/pyexpat.c:1441: warning: statement with no effect
extensions/pyexpat.c: In function ‘xmlparse_getattr’:
extensions/pyexpat.c:1452: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1454: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1454: error: lvalue required as increment operand
extensions/pyexpat.c:1454: warning: statement with no effect
extensions/pyexpat.c:1486: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1499: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1500: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1500: error: lvalue required as increment operand
extensions/pyexpat.c:1500: warning: statement with no effect
extensions/pyexpat.c:1504: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1504: error: lvalue required as increment operand
extensions/pyexpat.c:1504: warning: statement with no effect
extensions/pyexpat.c:1520: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1522: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1524: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1524: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1524: error: lvalue required as decrement operand
extensions/pyexpat.c:1524: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1524: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1524: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1524: warning: statement with no effect
extensions/pyexpat.c:1526: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1526: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1526: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1526: error: lvalue required as decrement operand
extensions/pyexpat.c:1526: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1526: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1526: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1526: warning: statement with no effect
extensions/pyexpat.c:1527: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1527: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1527: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1527: error: lvalue required as decrement operand
extensions/pyexpat.c:1527: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1527: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1527: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1527: warning: statement with no effect
extensions/pyexpat.c:1528: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1528: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1528: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1528: error: lvalue required as decrement operand
extensions/pyexpat.c:1528: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1528: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1528: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1528: warning: statement with no effect
extensions/pyexpat.c:1529: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1529: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1529: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1529: error: lvalue required as decrement operand
extensions/pyexpat.c:1529: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1529: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1529: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1529: warning: statement with no effect
extensions/pyexpat.c:1530: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1530: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1530: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1530: error: lvalue required as decrement operand
extensions/pyexpat.c:1530: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1530: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1530: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1530: warning: statement with no effect
extensions/pyexpat.c:1531: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1531: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1531: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1531: error: lvalue required as decrement operand
extensions/pyexpat.c:1531: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1531: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1531: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1531: warning: statement with no effect
extensions/pyexpat.c:1532: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1532: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1532: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1532: error: lvalue required as decrement operand
extensions/pyexpat.c:1532: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1532: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1532: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1532: warning: statement with no effect
extensions/pyexpat.c:1533: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1533: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1533: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1533: error: lvalue required as decrement operand
extensions/pyexpat.c:1533: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1533: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1533: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1533: warning: statement with no effect
extensions/pyexpat.c:1534: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1534: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1534: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1534: error: lvalue required as decrement operand
extensions/pyexpat.c:1534: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1534: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1534: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1534: warning: statement with no effect
extensions/pyexpat.c:1535: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1535: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1535: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1535: error: lvalue required as decrement operand
extensions/pyexpat.c:1535: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1535: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1535: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1535: warning: statement with no effect
extensions/pyexpat.c:1536: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1536: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1536: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1536: error: lvalue required as decrement operand
extensions/pyexpat.c:1536: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1536: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1536: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1536: warning: statement with no effect
extensions/pyexpat.c:1537: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1537: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1537: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1537: error: lvalue required as decrement operand
extensions/pyexpat.c:1537: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1537: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1537: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1537: warning: statement with no effect
extensions/pyexpat.c:1538: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1538: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1538: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1538: error: lvalue required as decrement operand
extensions/pyexpat.c:1538: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1538: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1538: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1538: warning: statement with no effect
extensions/pyexpat.c:1539: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1539: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1539: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1539: error: lvalue required as decrement operand
extensions/pyexpat.c:1539: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1539: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1539: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1539: warning: statement with no effect
extensions/pyexpat.c:1540: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1540: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1540: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1540: error: lvalue required as decrement operand
extensions/pyexpat.c:1540: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1540: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1540: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1540: warning: statement with no effect
extensions/pyexpat.c: In function ‘sethandler’:
extensions/pyexpat.c:1557: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1558: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1559: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1559: error: lvalue required as increment operand
extensions/pyexpat.c:1559: warning: statement with no effect
extensions/pyexpat.c:1563: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1563: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1563: error: lvalue required as decrement operand
extensions/pyexpat.c:1563: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1563: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1563: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1563: warning: statement with no effect
extensions/pyexpat.c: In function ‘xmlparse_setattr’:
extensions/pyexpat.c:1574: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1580: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1581: warning: incompatible implicit declaration of built-in function ‘malloc’
extensions/pyexpat.c:1582: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1589: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1593: warning: assignment from incompatible pointer type
extensions/pyexpat.c: In function ‘xmlparse_traverse’:
extensions/pyexpat.c:1654: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c: In function ‘xmlparse_clear’:
extensions/pyexpat.c:1668: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1668: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1668: error: lvalue required as decrement operand
extensions/pyexpat.c:1668: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1668: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1668: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1668: warning: statement with no effect
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:1677: warning: initialization makes pointer from integer without a cast
extensions/pyexpat.c:1677: error: initializer element is not constant
extensions/pyexpat.c:1677: error: (near initialization for ‘Xmlparsetype.ob_type’)
extensions/pyexpat.c:1680: warning: initialization makes pointer from integer without a cast
extensions/pyexpat.c: In function ‘pyexpat_ParserCreate’:
extensions/pyexpat.c:1722: warning: initialization from incompatible pointer type
extensions/pyexpat.c:1723: warning: initialization from incompatible pointer type
extensions/pyexpat.c:1724: warning: initialization from incompatible pointer type
extensions/pyexpat.c:1728: error: initializer element is not constant
extensions/pyexpat.c:1728: error: (near initialization for ‘kwlist[3]’)
extensions/pyexpat.c:1732: warning: return from incompatible pointer type
extensions/pyexpat.c:1734: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1734: warning: incompatible implicit declaration of built-in function ‘strlen’
extensions/pyexpat.c:1738: warning: return from incompatible pointer type
extensions/pyexpat.c:1743: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1744: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1747: warning: return from incompatible pointer type
extensions/pyexpat.c:1750: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1750: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1750: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1750: warning: passing argument 1 of ‘PyType_IsSubtype’ from incompatible pointer type
extensions/pyexpat.c:1752: warning: return from incompatible pointer type
extensions/pyexpat.c:1757: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1757: error: lvalue required as decrement operand
extensions/pyexpat.c:1757: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1757: error: request for member ‘tp_dealloc’ in something not a structure or union
extensions/pyexpat.c:1757: error: called object ‘*(char **)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1757: warning: statement with no effect
extensions/pyexpat.c: In function ‘pyexpat_ErrorString’:
extensions/pyexpat.c:1772: warning: return from incompatible pointer type
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:1784: error: initializer element is not constant
extensions/pyexpat.c:1784: error: (near initialization for ‘pyexpat_methods[2].ml_name’)
extensions/pyexpat.c:1784: error: initializer element is not constant
extensions/pyexpat.c:1784: error: (near initialization for ‘pyexpat_methods[2].ml_meth’)
extensions/pyexpat.c:1784: error: initializer element is not constant
extensions/pyexpat.c:1784: error: (near initialization for ‘pyexpat_methods[2].ml_doc’)
extensions/pyexpat.c: In function ‘get_version_string’:
extensions/pyexpat.c:1804: warning: implicit declaration of function ‘isdigit’
extensions/pyexpat.c:1809: warning: passing argument 2 of ‘PyString_FromStringAndSize’ makes pointer from integer without a cast
extensions/pyexpat.c: In function ‘initpyexpat’:
extensions/pyexpat.c:1842: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1845: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1855: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1857: warning: passing argument 2 of ‘PyErr_NewException’ from incompatible pointer type
extensions/pyexpat.c:1857: warning: passing argument 3 of ‘PyErr_NewException’ from incompatible pointer type
extensions/pyexpat.c:1858: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1861: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1861: error: lvalue required as increment operand
extensions/pyexpat.c:1861: warning: statement with no effect
extensions/pyexpat.c:1863: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1863: error: lvalue required as increment operand
extensions/pyexpat.c:1863: warning: statement with no effect
extensions/pyexpat.c:1892: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1894: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1900: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1900: error: lvalue required as decrement operand
extensions/pyexpat.c:1900: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1900: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1900: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1900: warning: statement with no effect
extensions/pyexpat.c:1902: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1904: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1910: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1910: error: lvalue required as decrement operand
extensions/pyexpat.c:1910: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1910: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1910: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1910: warning: statement with no effect
extensions/pyexpat.c:1911: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1911: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1919: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1928: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:1929: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1929: error: lvalue required as decrement operand
extensions/pyexpat.c:1929: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1929: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1929: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1929: warning: statement with no effect
extensions/pyexpat.c:1930: warning: assignment from incompatible pointer type
extensions/pyexpat.c:1934: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:1934: error: lvalue required as decrement operand
extensions/pyexpat.c:1934: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:1934: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:1934: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:1934: warning: statement with no effect
extensions/pyexpat.c:1940: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c: In function ‘clear_handlers’:
extensions/pyexpat.c:2025: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:2027: warning: assignment from incompatible pointer type
extensions/pyexpat.c:2030: warning: assignment from incompatible pointer type
extensions/pyexpat.c:2031: warning: comparison of distinct pointer types lacks a cast
extensions/pyexpat.c:2031: error: ‘PyObject’ has no member named ‘ob_refcnt’
extensions/pyexpat.c:2031: error: lvalue required as decrement operand
extensions/pyexpat.c:2031: error: ‘PyObject’ has no member named ‘ob_type’
extensions/pyexpat.c:2031: error: ‘struct PyMethodDef’ has no member named ‘tp_dealloc’
extensions/pyexpat.c:2031: error: called object ‘*(struct PyMethodDef *)&<erroneous-expression>’ is not a function
extensions/pyexpat.c:2031: warning: statement with no effect
extensions/pyexpat.c: At top level:
extensions/pyexpat.c:2107: error: initializer element is not constant
extensions/pyexpat.c:2107: error: (near initialization for ‘handler_info[22].name’)
extensions/pyexpat.c:2107: error: initializer element is not constant
extensions/pyexpat.c:2107: error: (near initialization for ‘handler_info[22].setter’)
extensions/pyexpat.c:2107: error: initializer element is not constant
extensions/pyexpat.c:2107: error: (near initialization for ‘handler_info[22].handler’)
error: command 'gcc' failed with exit status 1
kent@DOWN:~/Desktop/pyxml$
```
I can't even copy the whole thing, sorry.

---

### Post by crmccreary on 2008-07-20
I was able to download the source package from sourceforge, saved it in a directory, opened a shell, executed "python setup.py build", and it built OK. Of course you then need to execute "sudo python setup.py install" to install it.

---

### Post by pkchill88 on 2009-08-13
1)Downloaded pyXML. 
2)Unzipped it into a folder. 
3)Navigated to the folder
4)python setup.py build
Supposed to compile all the .c files.
But i get a series of lines like 

> extensions/pyexpat.c:2029: error: ‘xmlparseobject’ has no member named ‘handlers’
ending with 

> error: command 'gcc' failed with exit status 1

What am i supposed to do?

---

### Post by crmccreary on 2009-08-13
Building pyXML is a pain unless you have all of the python headers and such. In my earlier post, I must have been on my development machine which had all of the pre-requisites. I just tried to build it on a Hardy machine with no luck. Have you tried 
```

sudo apt-get install python-xml

```
to get a built version from the repos? It will have the pre-built pyexpat.

If you are using this module in new code, I would advise against it as pyXML is no longer maintained. Use elementTree instead.

---

### Post by pkchill88 on 2009-09-15
yeah i got the point. pyXML is no longer maintained and fails to work with ver 2.5 and above. 

Thank you

---

