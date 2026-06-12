---
title: "JavaScript escape function in C++"
date: 2009-09-02
forum: Programming Talk
---

### Post by WitchCraft on 2009-09-02
Hi, I need a little help converting the below Delphi function into C++:

I need an equivalent of JavaScript's escape function in C++.

I've converted it without problems to C# and VB.NET, but in C++, I somehow always get @ when I have a non-ascii character...

See 
[http://forums.asp.net/p/1308104/3380222.aspx](http://forums.asp.net/p/1308104/3380222.aspx)
for the .NET version

```

function wideescape(s: widestring): string;
var I: integer;
begin
result := '';
for I := 1 to length(s) do
if ((s[i] >= 'A') and (s[i] <= 'z')) or ((s[i] >= '0') and (s[i] <= '9'))
or (s[i] = '@') or (s[i] = '*') or (s[i] = '-') or (s[i] = '_') or (s[i] = '+') or (s[i] = '.') or (s[i] = '/') then
result := result + s[i]
else
if s[i] < widechar(256) then
result := result + '%' + IntToHex(byte(s[i]), 2)
else
result := result + '&#x' + IntToHex(word(s[i]), 4);
end

```

Here is what I have done so far:
```

#include <iostream>
#include <cstdlib>


std::wstring wideescape(std::wstring s)
{
    int i;
    std::wstring wstrResult = L"";

    for (i = 0; i < s.length();++i)
    {
        if ( ((s[i] >= L'A') && (s[i] <= L'z')) || ((s[i] >= L'0') && (s[i] <= L'9')) || (s[i] = L'@') ||
                (s[i] = L'*') || (s[i] = L'-') || (s[i] = L'_') || (s[i] = L'+') || (s[i] = L'.') || (s[i] = L'/') )
            wstrResult += s[i] ;
        else
        {
            if (s[i] < (wchar_t) 256 )
            {
                wchar_t temp[4];
                swprintf(temp,4, L"\%%02X",(int)s[i]) ;
                // wcscpy(temp,L"te"); // doesn't even get called...
                wstrResult += temp ;
                //result := result + '%' + IntToHex(byte(s[i]), 2)
            }
            else
            {
                wchar_t temp[8];
                //swprintf(temp,8,L"&#x%04X",(int)s[i]) ;
                // wcscpy(temp,L"hello"); //  doesn't even get called
                wstrResult += temp ;
                //wstrResult += L"&#x" + IntToHex(word(s[i]), 4);
            }
		}
    }
    return wstrResult;
}

int main()
{
    std::wstring test = L"Testäöü^ !';.-<>{}" ;
    test= wideescape(test);
    wprintf(L"Test: %ls\n", test.c_str());
    return EXIT_FAILURE ;
}


```

---

### Post by WitchCraft on 2009-09-02
Oh crap, i used = instead of == lol

Damn, I realize I've been programming in other languages too much...

New Version:
```

#include <iostream>
#include <cstdlib>
#include <string>


// Port of the JavaScript escape function from Delphi to C++
std::wstring wideescape(std::wstring s)
{
    int i;
    std::wstring wstrResult = L"";
    for (i = 0; i < s.length(); ++i)
    {
        if (((s[i] >= 'A') && (s[i] <= 'z')) || ((s[i] >= '0') && (s[i] <= '9')) || (s[i] == '@') || (s[i] == '*') || (s[i] == '-') || (s[i] == '_') || (s[i] == '+') || (s[i] == '.') || (s[i] == '/') )
            wstrResult += s[i] ;
        else
        {
            if (s[i] < (wchar_t) 256 )
            {
                wchar_t wszTemp[4];
                swprintf(wszTemp, 4, L"%%%02X", (int) s[i] );
                wstrResult +=wszTemp;
                //wstrResult += "%" + IntToHex(byte(s[i]), 2);
            }
            else
            {
                wchar_t wszTemp[8];
                swprintf(wszTemp, 8, L"&#x%04X", (int) s[i] );
                wstrResult +=wszTemp;
                //wstrResult += "&#x" + IntToHex(word(s[i]), 4);
            }
        }
    }

    return wstrResult;
}



int main()
{
    std::wstring wstrTest = L"Testöäü'?~^\"[]{};,.:-_" ;
    wstrTest=wideescape(wstrTest);
    wprintf(L"Test: %ls\n", wstrTest.c_str());
}

```

---

### Post by WitchCraft on 2009-09-03
Still buggy, and I didn't know the source.

So I searched for them:

[http://mxr.mozilla.org/seamonkey/source/js/src/jsstr.c](http://mxr.mozilla.org/seamonkey/source/js/src/jsstr.c)

Looks like it is a bit more complex:

```

241 
242 /*
243  * Forward declarations for URI encode/decode and helper routines
244  */
245 static JSBool
246 str_decodeURI(JSContext *cx, uintN argc, jsval *vp);
247 
248 static JSBool
249 str_decodeURI_Component(JSContext *cx, uintN argc, jsval *vp);
250 
251 static JSBool
252 str_encodeURI(JSContext *cx, uintN argc, jsval *vp);
253 
254 static JSBool
255 str_encodeURI_Component(JSContext *cx, uintN argc, jsval *vp);
256 
257 static uint32
258 Utf8ToOneUcs4Char(const uint8 *utf8Buffer, int utf8Length);
259 
260 /*
261  * Contributions from the String class to the set of methods defined for the
262  * global object.  escape and unescape used to be defined in the Mocha library,
263  * but as ECMA decided to spec them, they've been moved to the core engine
264  * and made ECMA-compliant.  (Incomplete escapes are interpreted as literal
265  * characters by unescape.)
266  */
267 
268 /*
269  * Stuff to emulate the old libmocha escape, which took a second argument
270  * giving the type of escape to perform.  Retained for compatibility, and
271  * copied here to avoid reliance on net.h, mkparse.c/NET_EscapeBytes.
272  */
273 
274 #define URL_XALPHAS     ((uint8) 1)
275 #define URL_XPALPHAS    ((uint8) 2)
276 #define URL_PATH        ((uint8) 4)
277 
278 static const uint8 urlCharType[256] =
279 /*      Bit 0           xalpha          -- the alphas
280  *      Bit 1           xpalpha         -- as xalpha but
281  *                             converts spaces to plus and plus to %20
282  *      Bit 2 ...       path            -- as xalphas but doesn't escape '/'
283  */
284     /*   0 1 2 3 4 5 6 7 8 9 A B C D E F */
285     {    0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,       /* 0x */
286          0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,       /* 1x */
287          0,0,0,0,0,0,0,0,0,0,7,4,0,7,7,4,       /* 2x   !"#$%&'()*+,-./  */
288          7,7,7,7,7,7,7,7,7,7,0,0,0,0,0,0,       /* 3x  0123456789:;<=>?  */
289          7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,       /* 4x  @ABCDEFGHIJKLMNO  */
290          7,7,7,7,7,7,7,7,7,7,7,0,0,0,0,7,       /* 5X  PQRSTUVWXYZ[\]^_  */
291          0,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,       /* 6x  `abcdefghijklmno  */
292          7,7,7,7,7,7,7,7,7,7,7,0,0,0,0,0,       /* 7X  pqrstuvwxyz{\}~  DEL */
293          0, };
294 
295 /* This matches the ECMA escape set when mask is 7 (default.) */
296 
297 #define IS_OK(C, mask) (urlCharType[((uint8) (C))] & (mask))
298 
299 /* See ECMA-262 Edition 3 B.2.1 */
300 JSBool
301 js_str_escape(JSContext *cx, JSObject *obj, uintN argc, jsval *argv, jsval *rval)
302 {
303     JSString *str;
304     size_t i, ni, length, newlength;
305     const jschar *chars;
306     jschar *newchars;
307     jschar ch;
308     jsint mask;
309     jsdouble d;
310     const char digits[] = {'0', '1', '2', '3', '4', '5', '6', '7',
311                            '8', '9', 'A', 'B', 'C', 'D', 'E', 'F' };
312 
313     mask = URL_XALPHAS | URL_XPALPHAS | URL_PATH;
314     if (argc > 1) {
315         d = js_ValueToNumber(cx, &argv[1]);
316         if (JSVAL_IS_NULL(argv[1]))
317             return JS_FALSE;
318         if (!JSDOUBLE_IS_FINITE(d) ||
319             (mask = (jsint)d) != d ||
320             mask & ~(URL_XALPHAS | URL_XPALPHAS | URL_PATH))
321         {
322             char numBuf[12];
323             JS_snprintf(numBuf, sizeof numBuf, "%lx", (unsigned long) mask);
324             JS_ReportErrorNumber(cx, js_GetErrorMessage, NULL,
325                                  JSMSG_BAD_STRING_MASK, numBuf);
326             return JS_FALSE;
327         }
328     }
329 
330     str = js_ValueToString(cx, argv[0]);
331     if (!str)
332         return JS_FALSE;
333     argv[0] = STRING_TO_JSVAL(str);
334 
335     JSSTRING_CHARS_AND_LENGTH(str, chars, length);
336     newlength = length;
337 
338     /* Take a first pass and see how big the result string will need to be. */
339     for (i = 0; i < length; i++) {
340         if ((ch = chars[i]) < 128 && IS_OK(ch, mask))
341             continue;
342         if (ch < 256) {
343             if (mask == URL_XPALPHAS && ch == ' ')
344                 continue;   /* The character will be encoded as '+' */
345             newlength += 2; /* The character will be encoded as %XX */
346         } else {
347             newlength += 5; /* The character will be encoded as %uXXXX */
348         }
349 
350         /*
351          * This overflow test works because newlength is incremented by at
352          * most 5 on each iteration.
353          */
354         if (newlength < length) {
355             js_ReportAllocationOverflow(cx);
356             return JS_FALSE;
357         }
358     }
359 
360     if (newlength >= ~(size_t)0 / sizeof(jschar)) {
361         js_ReportAllocationOverflow(cx);
362         return JS_FALSE;
363     }
364 
365     newchars = (jschar *) JS_malloc(cx, (newlength + 1) * sizeof(jschar));
366     if (!newchars)
367         return JS_FALSE;
368     for (i = 0, ni = 0; i < length; i++) {
369         if ((ch = chars[i]) < 128 && IS_OK(ch, mask)) {
370             newchars[ni++] = ch;
371         } else if (ch < 256) {
372             if (mask == URL_XPALPHAS && ch == ' ') {
373                 newchars[ni++] = '+'; /* convert spaces to pluses */
374             } else {
375                 newchars[ni++] = '%';
376                 newchars[ni++] = digits[ch >> 4];
377                 newchars[ni++] = digits[ch & 0xF];
378             }
379         } else {
380             newchars[ni++] = '%';
381             newchars[ni++] = 'u';
382             newchars[ni++] = digits[ch >> 12];
383             newchars[ni++] = digits[(ch & 0xF00) >> 8];
384             newchars[ni++] = digits[(ch & 0xF0) >> 4];
385             newchars[ni++] = digits[ch & 0xF];
386         }
387     }
388     JS_ASSERT(ni == newlength);
389     newchars[newlength] = 0;
390 
391     str = js_NewString(cx, newchars, newlength);
392     if (!str) {
393         JS_free(cx, newchars);
394         return JS_FALSE;
395     }
396     *rval = STRING_TO_JSVAL(str);
397     return JS_TRUE;
398 }
399 #undef IS_OK
400 
401 static JSBool
402 str_escape(JSContext *cx, uintN argc, jsval *vp)
403 {
404     JSObject *obj;
405 
406     obj = JS_THIS_OBJECT(cx, vp);
407     return obj && js_str_escape(cx, obj, argc, vp + 2, vp);
408 }
409 
410 /* See ECMA-262 Edition 3 B.2.2 */
411 static JSBool
412 str_unescape(JSContext *cx, uintN argc, jsval *vp)
413 {
414     JSString *str;
415     size_t i, ni, length;
416     const jschar *chars;
417     jschar *newchars;
418     jschar ch;
419 
420     str = js_ValueToString(cx, vp[2]);
421     if (!str)
422         return JS_FALSE;
423     vp[2] = STRING_TO_JSVAL(str);
424 
425     JSSTRING_CHARS_AND_LENGTH(str, chars, length);
426 
427     /* Don't bother allocating less space for the new string. */
428     newchars = (jschar *) JS_malloc(cx, (length + 1) * sizeof(jschar));
429     if (!newchars)
430         return JS_FALSE;
431     ni = i = 0;
432     while (i < length) {
433         ch = chars[i++];
434         if (ch == '%') {
435             if (i + 1 < length &&
436                 JS7_ISHEX(chars[i]) && JS7_ISHEX(chars[i + 1]))
437             {
438                 ch = JS7_UNHEX(chars[i]) * 16 + JS7_UNHEX(chars[i + 1]);
439                 i += 2;
440             } else if (i + 4 < length && chars[i] == 'u' &&
441                        JS7_ISHEX(chars[i + 1]) && JS7_ISHEX(chars[i + 2]) &&
442                        JS7_ISHEX(chars[i + 3]) && JS7_ISHEX(chars[i + 4]))
443             {
444                 ch = (((((JS7_UNHEX(chars[i + 1]) << 4)
445                         + JS7_UNHEX(chars[i + 2])) << 4)
446                       + JS7_UNHEX(chars[i + 3])) << 4)
447                     + JS7_UNHEX(chars[i + 4]);
448                 i += 5;
449             }
450         }
451         newchars[ni++] = ch;
452     }
453     newchars[ni] = 0;
454 
455     str = js_NewString(cx, newchars, ni);
456     if (!str) {
457         JS_free(cx, newchars);
458         return JS_FALSE;
459     }
460     *vp = STRING_TO_JSVAL(str);
461     return JS_TRUE;
462 }

```

---

