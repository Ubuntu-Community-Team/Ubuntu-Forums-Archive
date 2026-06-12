---
title: "[C++] use of enum without previous declaration"
date: 2009-07-29
forum: Programming Talk
---

### Post by wbest on 2009-07-29
Hey, I'm maintaining some code, and g++ doesn't like the way its currently written.
So I need a bit of help figuring out the best way to fix this problem.
I keep getting the error:

** error: use of enum &#8216;CMLEvent&#8217; without previous declaration**

The code is (I cut out some unimportant parts) with the error line:

```
#ifndef _CMLTYPES_H 
#define _CMLTYPES_H 
 
#include "tw_cml_api.h" 
 
#include "CMLDayCount.h" 
#include "CMLExceptions.h" 
#include "CMLTypeBase.h"
 
enum CMLEvent //THIS IS THE LINE WITH THE ERROR; 
 
/*
const CMLCalc declarations used to be here
*/ 
 
enum CMLSecClass 
{ 
    S_Null, 
    S_Bond, 
    S_ZBond, 
    S_Discount, 
    S_FloatingRateNote, 
    S_IndexLinkedBond, 
}; 
 
enum CMLAnalytics 
{ 
    A_PriceYield=1, 
    A_Accrual, 
    A_CashFlow, 
    A_HorizonReturn, 
    A_CostOfCarry, 
    A_OptionAdjustedSpread, 
    A_Sensitivity, 
    A_Volatility, 
}; 
 
enum CMLPriceFormat 
{ 
    P_Decimal, 
    P_32nd, 
    P_DefaultOfCurrency 
}; 
 
enum CMLTradingBasis 
{ 
    TB_Price, 
    TB_Yield, 
    TB_DiscountRate, 
    TB_Spread, 
    TB_OAS, 
}; 
 
enum CMLYieldCurveType 
{ 
    ParCurve, 
    SpotCurve, 
}; 
 
 
#endif    //_CMLTYPES_H 
```

---

### Post by Zugzwang on 2009-07-29
The question here is: What is that line supposed to do?

If its aim is to declare an "enum" without any elements, add braces:
```

enum foo {};

```

---

### Post by wbest on 2009-07-29
Right, no, see the trick is its defined elsewhere.
So adding braces returns a multiple definition error.

---

