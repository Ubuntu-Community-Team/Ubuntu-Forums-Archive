---
title: "from QBASIC to C"
date: 2010-02-05
forum: Programming Talk
---

### Post by geonomica on 2010-02-05
hy list,
I need help in convert about 350 QBASIC code line in C language. I don't know in deep QBASIC and the code I have to translate has a huge amount of GOTO/LABEL.
Could anybody help me for translate code listed below:

(I need really help!!!](*,)
by
geo

CLS
10 popa = 92: pop = 18: c = 10: at = 0: DIM a(pop, c + at + 1): DIM rulea(400, c + at + 1): DIM ruleb(400, c + at + 1): DIM lower(pop): d = -1: csoglia = .75: DIM credrul(400): DIM b(c + at): tSUP = 0: DIM impa(c): DIM impc(c, 5): DIM credrulb(400): DIM scored(popa): DIM scorefd(popa): DIM scoretd(popa)

OPEN "alm1N" FOR OUTPUT AS #1

DATA    1.0000  ,       0.0000  ,       0.7597  ,       953     ,       0.0409  ,       0.010721757     ,       8.43731432      ,       0       ,       0.017467054     ,       0.003053596     ,       3
DATA    1.0000  ,       0.0000  ,       0.7471  ,       670     ,       0.1045  ,       0.010983264     ,       2.477477477     ,       4.524687828     ,       0.273262237     ,       0       ,       3
DATA    1.0000  ,       0.0000  ,       0.7428  ,       817     ,       0.0514  ,       0.012813808     ,       0.475030451     ,       1.769992196     ,       0.193626285     ,       0.156161584     ,       3
DATA    1.0000  ,       0.0000  ,       0.6260  ,       1208    ,       0.0522  ,       0.012552301     ,       1.017068038     ,       1.802027954     ,       0.84098986      ,       0.01373486      ,       3
DATA    1.0000  ,       0.0000  ,       0.8493  ,       681     ,       0.0675  ,       0.013075314     ,       0.292302696     ,       0       ,       0.701464423     ,       0.108533659     ,       3
DATA    0.7826  ,       17.6521 ,       0.8225  ,       5630    ,       0.0448  ,       0.010983264     ,       1.110470147     ,       37.20977507     ,       1.029587786     ,       0.003298422     ,       3
DATA    0.4709  ,       13.7346 ,       0.7914  ,       1682    ,       0.0559  ,       0.009675732     ,       1.49691358      ,       0.300095602     ,       0.206558161     ,       0.038562285     ,       2
DATA    0.2909  ,       76.8441 ,       0.7532  ,       37889   ,       0.0164  ,       0.012290795     ,       1.401481566     ,       0.492518237     ,       1.126052341     ,       0.047641968     ,       2
DATA    0.3045  ,       41.8793 ,       0.7663  ,       31616   ,       0.0201  ,       0.011506276     ,       1.925420888     ,       6.089170195     ,       0.500778839     ,       0.069858794     ,       2
DATA    0.3203  ,       74.2411 ,       0.7856  ,       7773    ,       0.0277  ,       0.012029289     ,       2.529510961     ,       95.03157742     ,       0.432568678     ,       0.049547539     ,       2
DATA    0.6825  ,       12.3115 ,       0.8236  ,       2649    ,       0.0434  ,       0.009414226     ,       2.532572098     ,       0.297094837     ,       0.195260701     ,       0.028741803     ,       2
DATA    0.3654  ,       76.8147 ,       0.7350  ,       3952    ,       0.0195  ,       0.011506276     ,       2.940275651     ,       78.66160892     ,       0.688601844     ,       0.027709895     ,       2
DATA    0.3261  ,       79.4602 ,       0.8158  ,       1791    ,       0.0140  ,       0.00915272      ,       0.526662278     ,       11.3960114      ,       0.350763416     ,       0       ,       1
DATA    0.0694  ,       151.3876        ,       0.7176  ,       1700    ,       0.0094  ,       0.00915272      ,       0       ,       5.803899273     ,       0.29419314      ,       0       ,       1
DATA    0.1107  ,       294.7680        ,       0.7573  ,       149125  ,       0.0103  ,       0.011506276     ,       2.004800853     ,       75.78508313     ,       0.744131117     ,       0.029912018     ,       1
DATA    0.0755  ,       615.8943        ,       0.7685  ,       18400   ,       0.0106  ,       0.01124477      ,       1.086169442     ,       68.56187473     ,       2.402253412     ,       0.009938796     ,       1
DATA    0.1129  ,       92.9789 ,       0.9144  ,       1045    ,       0.0124  ,       0.00915272      ,       0       ,       51.81270448     ,       0.159075365     ,       0       ,       1
DATA    0.0968  ,       447.6121        ,       0.7370  ,       105018  ,       0.0045  ,       0.00915272      ,       0.297310052     ,       4.22529746      ,       6.415647972     ,       0.010683966     ,       1

FOR h = 1 TO pop
FOR j = 1 TO c + at + 1
PRINT h;
READ a(h, j)
PRINT a(h, j);
a(h, j) = -a(h, j)
IF j = 2 THEN a(h, j) = -a(h, j)
IF j = 3 THEN a(h, j) = -a(h, j)
IF j = 4 THEN a(h, j) = -a(h, j)
IF j = 8 THEN a(h, j) = -a(h, j)
IF j = 9 THEN a(h, j) = -a(h, j)


NEXT j
PRINT " "
NEXT h
CLS

REM FOR h = 1 TO pop
REM PRINT h, ":"
REM FOR J = 1 TO c
REM a(h, J) = 6 - a(h, J)
REM PRINT a(h, J);
REM NEXT J
REM PRINT
REM NEXT h

REM 5500 FOR h = 1 TO pop
REM 5510 FOR J = 1 TO c + at + 1
REM 5520 IF a(h, J) > 5 THEN a(h, J) = 6
REM 5530 NEXT J
REM 5540 NEXT h

5600 FOR t = 1 TO 400
5610 FOR j = 1 TO c + at
5620 rulea(t, j) = 1000
5630 NEXT j
5640 NEXT t
6000 FOR j = 1 TO c + at
6010 IF b(j) = 0 THEN b(j) = 1: LAST = j - 1: GOTO 6040
6020 NEXT j

FOR j = 1 TO c
PRINT "domanda", j, impa(j)
WRITE #1, "domanda", j, impa(j)
NEXT j

GOTO 100000

FOR j = 1 TO c
FOR ty = 1 TO 5
IF impc(j, ty) > 0 THEN PRINT "domanda", j, "valutazione", ty, impc(j, ty)
WRITE #1, "domanda", j, impa(j), "valutazione", ty, impc(j, ty)
NEXT ty
NEXT j
CLOSE

6030 END

6040 FOR j = 1 TO LAST
6050 b(j) = 0
6060 NEXT j
6070 FOR h = 1 TO pop
6080 lower(h) = 0
6090 NEXT h
7000 FOR h = 1 TO pop
7005 IF a(h, c + at + 1) = 0 THEN GOTO 7090
7006 IF a(h, c + at + 1) < d THEN GOTO 7090
7010 FOR k = 1 TO pop
7015 IF a(k, c + at + 1) = 0 THEN GOTO 7080
7020 FOR j = 1 TO c
7030 IF b(j) = 0 THEN GOTO 7050
REM 7035 IF a(h, J) = 6 THEN GOTO 7090
7040 IF a(h, j) > a(k, j) THEN GOTO 7080
7050 NEXT j
7051 FOR j = c + 1 TO c + at
7052 IF b(j) = 0 THEN GOTO 7056
REM 7053 IF a(h, J) = 6 THEN GOTO 7090
REM 7054 IF a(k, J) = 6 THEN GOTO 7056
7055 IF a(h, j) <> a(k, j) THEN GOTO 7080
7056 NEXT j
7061 IF a(k, c + at + 1) < d THEN contr = contr + 1
7062 IF a(k, c + at + 1) >= d THEN corr = corr + 1
7080 NEXT k
7085 lower(h) = corr / (contr + corr): contr = 0: corr = 0
7090 NEXT h
8000 FOR h = 1 TO pop
8010 IF lower(h) < csoglia THEN GOTO 12380
8020 FOR t = 1 TO rule
8030 FOR j = 1 TO c
8040 IF b(j) = 0 AND rulea(t, j) = 1000 THEN GOTO 8070
8050 IF b(j) = 0 THEN GOTO 8090
8055 IF rulea(t, j) = 1000 THEN GOTO 8070
8060 IF rulea(t, j) > a(h, j) THEN GOTO 8090
8070 NEXT j
8071 FOR j = c + 1 TO c + at
8072 IF b(j) = 0 AND rulea(t, j) = 1000 THEN GOTO 8076
8073 IF b(j) = 0 THEN GOTO 8090
8074 IF rulea(t, j) = 1000 THEN GOTO 8076
8075 IF rulea(t, j) <> a(h, j) THEN GOTO 8090
8076 NEXT j
8080 IF credrul(t) >= lower(h) THEN GOTO 12380
8090 NEXT t
9020 FOR k = 1 TO pop
9040 IF k = h THEN GOTO 9140
9050 IF lower(k) < lower(h) THEN GOTO 9140
9060 FOR j = 1 TO c
9070 IF b(j) = 0 THEN GOTO 9090
9080 IF a(h, j) < a(k, j) THEN GOTO 9140
9090 NEXT j
9091 FOR j = c + 1 TO c + at
9092 IF b(j) = 0 THEN GOTO 9094
9093 IF a(h, j) <> a(k, j) THEN GOTO 9140
9094 NEXT j
9100 FOR j = 1 TO c
9110 IF b(j) = 0 THEN GOTO 9130
9120 IF a(h, j) <> a(k, j) THEN GOTO 12380
9130 NEXT j
9140 NEXT k
9150 rule = rule + 1: credrul(rule) = lower(h)
10100 FOR j = 1 TO c + at
10120 IF b(j) = 0 THEN GOTO 10140
10130 rulea(rule, j) = a(h, j)
10140 NEXT j
11080 FOR l = 1 TO pop
11085 IF a(l, c + at + 1) = 0 THEN GOTO 11140
11090 FOR j = 1 TO c
11100 IF rulea(rule, j) = 1000 THEN GOTO 11120
11101 IF a(l, j) = 1000 THEN GOTO 11140
11110 IF rulea(rule, j) > a(l, j) THEN GOTO 11140
11120 NEXT j
11121 FOR j = c + 1 TO c + at
11122 IF rulea(rule, j) = 1000 THEN GOTO 11125
11123 IF a(l, j) = 1000 THEN GOTO 11140
11124 IF rulea(rule, j) <> a(l, j) THEN GOTO 11140
11125 NEXT j
11135 tot = tot + 1
11140 NEXT l
11155 sup = tot / pop
11156 tot = 0
12140 IF sup < tSUP THEN GOTO 12380
12150 rp = rp + 1: PRINT rp;
FOR j = 1 TO c
ruleb(rp, j) = rulea(rule, j)
NEXT j
credrulb(rp) = credrul(rule)

WRITE #1, "regola n."
    WRITE #1, rp
12160 PRINT credrul(rule);
    WRITE #1, "conf."
      WRITE #1, credrul(rule)
12170 PRINT "    ;";
	WRITE #1, "    ;"


12180 FOR j = 1 TO c + at
12190 IF rulea(rule, j) < 1000 THEN PRINT rulea(rule, j);
IF rulea(rule, j) < 1000 THEN WRITE #1, "domanda": impa(j) = impa(j) + 1
IF rulea(rule, j) < 1000 THEN WRITE #1, j
IF rulea(rule, j) < 1000 THEN WRITE #1, rulea(rule, j)
12200 IF rulea(rule, j) = 1000 THEN PRINT "*";
REM IF rulea(rule, j) < 1000 THEN WRITE #1, "*"
12210 NEXT j
12220 PRINT "  "
WRITE #1, "    "

12230 FOR l = 1 TO pop
12240 IF a(l, c + at + 1) = 0 THEN GOTO 12350
12250 FOR j = 1 TO c
12255 IF rulea(rule, j) = 1000 THEN GOTO 12280
12260 IF a(l, j) = 1000 AND a(l, c + at + 1) < d THEN nn = nn + 1: GOTO 12350
IF a(l, j) = 1000 AND a(l, c + at + 1) >= d THEN np = np + 1: GOTO 12350
12270 IF rulea(rule, j) > a(l, j) AND a(l, c + at + 1) < d THEN nn = nn + 1: GOTO 12350
IF rulea(rule, j) > a(l, j) AND a(l, c + at + 1) >= d THEN np = np + 1: GOTO 12350
12280 NEXT j
12290 FOR j = c + 1 TO c + at
12295 IF rulea(rule, j) = 1000 THEN GOTO 12320
12300 IF a(l, j) = 1000 AND a(l, c + at + 1) < d THEN nn = nn + 1: GOTO 12350
IF a(l, j) = 1000 AND a(l, c + at + 1) >= d THEN np = np + 1: GOTO 12350
12310 IF rulea(rule, j) <> a(l, j) AND a(l, c + at + 1) < d THEN nn = nn + 1: GOTO 12350
IF rulea(rule, j) <> a(l, j) AND a(l, c + at + 1) >= d THEN np = np + 1: GOTO 12350
12320 NEXT j
12330 PRINT l;
WRITE #1, l
12340 IF a(l, c + at + 1) < d THEN pn = pn + 1: PRINT "(*)";
IF a(l, c + at + 1) < d THEN WRITE #1, "(*)"
IF a(l, c + at + 1) >= d THEN pp = pp + 1
12350 NEXT l
12360 PRINT "  "
WRITE #1, "  "
12370 PRINT sup
WRITE #1, "sup."
WRITE #1, sup
PRINT "nn", nn;
PRINT "np", np;
PRINT "pn", pn;
PRINT "pp", pp;
WRITE #1, "nn", nn, "np", np, "pn", pn, "pp", pp
dc = pp / (pp + pn) - (pp + np) / pop
REM lc = LOG((pp / (pp + pn)) - LOG((pp + np) / pop))
REM rc = LOG((pp / (np + pp)) - LOG(pn / (nn + pn)))
REM fc = ((pp / (np + pp)) - (pn / (nn + pn))) / ((pp / (np + pp)) + (pn / (nn + pn)))
REM sc = pp / (pp + pn) - np / (np + nn)
REM bc = pp / (pp + pn) - ((pp + np) * (pn + nn) / pop ^ 2)
REM ps = ABS(pp - (pp + pn) * (np + pp) / pop)
PRINT dc
REM PRINT dc, lc, rc, fc, sc, bc, ps
WRITE #1, "dc", dc
REM WRITE #1, "dc", dc, "lc", lc, "rc", rc, "fc", fc, "sc", sc, "bc", bc, "ps", ps
nn = 0: pp = 0: np = 0: pn = 0
12380 NEXT h
12390 GOTO 6000

100000 popa = 92: DIM ap(popa, c): DIM crd(popa)

DATA    0.2886  ,       96.3445 ,       0.7593  ,       25304   ,       0.0196  ,       0.011506276     ,       4.865125241     ,       34.40989097     ,       0.523870977     ,       0.02029675
DATA    0.0755  ,       615.8943        ,       0.7685  ,       18400   ,       0.0106  ,       0.01124477      ,       1.086169442     ,       68.56187473     ,       2.402253412     ,       0.009938796
DATA    0.6073  ,       32.8761 ,       0.7918  ,       3784    ,       0.0447  ,       0.01124477      ,       2.632743363     ,       162.0442561     ,       9.566516249     ,       0.002703335
DATA    0.4668  ,       45.5662 ,       0.8200  ,       4799    ,       0.0302  ,       0.01124477      ,       4.433760684     ,       47.20482789     ,       0.316827474     ,       0.010980974
DATA    0.2019  ,       37.9165 ,       0.7693  ,       2367    ,       0.0249  ,       0.01124477      ,       1.003613007     ,       4.704372332     ,       0.409006748     ,       0.01682126
DATA    0.3654  ,       76.8147 ,       0.7350  ,       3952    ,       0.0195  ,       0.011506276     ,       2.940275651     ,       78.66160892     ,       0.688601844     ,       0.027709895
DATA    0.5353  ,       8.3660  ,       0.8112  ,       3260    ,       0.0525  ,       0.013075314     ,       0.392070241     ,       0.15181053      ,       0.391474321     ,       0.05355749
DATA    0.6460  ,       48.2468 ,       0.7285  ,       3071    ,       0.0290  ,       0.010983264     ,       2.352418997     ,       0.331330624     ,       0.333490899     ,       0.001330845
DATA    0.4101  ,       40.8388 ,       0.7556  ,       14230   ,       0.0410  ,       0.013075314     ,       4.981998638     ,       4.1573074       ,       1.453636299     ,       0.007952534
DATA    1.0000  ,       0.0000  ,       0.7885  ,       1137    ,       0.0440  ,       0.012552301     ,       0.615055489     ,       11.02691349     ,       1.225719941     ,       0.007268908
DATA    0.5337  ,       60.3306 ,       0.7445  ,       3131    ,       0.0591  ,       0.010983264     ,       0.330578512     ,       33.92676745     ,       0.395304248     ,       0.445202621
DATA    0.2402  ,       48.5858 ,       0.7898  ,       7122    ,       0.0170  ,       0.010721757     ,       3.986710963     ,       8.709275378     ,       0.279560732     ,       0.128033856
DATA    0.2912  ,       69.2979 ,       0.7695  ,       37889   ,       0.0302  ,       0.012029289     ,       1.027017263     ,       97.29593014     ,       0.322665439     ,       0.027790816
DATA    0.6869  ,       16.4307 ,       0.7982  ,       2929    ,       0.0731  ,       0.010721757     ,       2.275577853     ,       68.39225625     ,       0.371098087     ,       0.014815639
DATA    0.3644  ,       152.2531        ,       0.7876  ,       15256   ,       0.0103  ,       0.010983264     ,       2.920395667     ,       14.0884971      ,       0.661472176     ,       0.02556098
DATA    0.5446  ,       14.2131 ,       0.8619  ,       1289    ,       0.0318  ,       0.011506276     ,       0.677966102     ,       0       ,       0.782705791     ,       0.252709794
DATA    0.3004  ,       127.5062        ,       0.8004  ,       8090    ,       0.0313  ,       0.011506276     ,       1.509348952     ,       152.7415289     ,       0.64264762      ,       0.00141849
DATA    0.1454  ,       165.6633        ,       0.7402  ,       51130   ,       0.0107  ,       0.01333682      ,       0.235053266     ,       13.37290178     ,       0.376155041     ,       0.035798698
DATA    0.3366  ,       45.8357 ,       0.8353  ,       2439    ,       0.0119  ,       0.011506276     ,       0.169971671     ,       28.48429048     ,       0.208795244     ,       0.016471976
DATA    0.6971  ,       29.9658 ,       0.8052  ,       1733    ,       0.0629  ,       0.010721757     ,       1.312785388     ,       136.823061      ,       0.388745595     ,       0
DATA    0.5421  ,       34.8638 ,       0.8082  ,       3383    ,       0.0405  ,       0.010983264     ,       1.80058519      ,       2.112289591     ,       0.786805438     ,       0.008877139
DATA    0.7467  ,       15.8487 ,       0.8265  ,       6056    ,       0.0469  ,       0.010721757     ,       1.539415229     ,       15.37846375     ,       0.25105502      ,       0.002856971
DATA    0.2960  ,       85.3933 ,       0.7613  ,       15064   ,       0.0128  ,       0.011767782     ,       0.611965537     ,       2.662115471     ,       0.285613994     ,       0.041713542
DATA    0.3045  ,       41.8793 ,       0.7663  ,       31616   ,       0.0201  ,       0.011506276     ,       1.925420888     ,       6.089170195     ,       0.500778839     ,       0.069858794
DATA    1.0000  ,       0.0000  ,       0.7471  ,       670     ,       0.1045  ,       0.010983264     ,       2.477477477     ,       4.524687828     ,       0.273262237     ,       0
DATA    0.2928  ,       67.0441 ,       0.8074  ,       12306   ,       0.0184  ,       0.012552301     ,       2.280255758     ,       10.07828584     ,       1.002064597     ,       0.054019034
DATA    0.4374  ,       56.8926 ,       0.8124  ,       16336   ,       0.0406  ,       0.010983264     ,       1.225626741     ,       80.24896626     ,       1.431998712     ,       0.0569301
DATA    0.7292  ,       12.2776 ,       0.7711  ,       3541    ,       0.0240  ,       0.01124477      ,       1.741134298     ,       1.290180769     ,       0.994425224     ,       0.001247175
DATA    1.0000  ,       0.0000  ,       0.8114  ,       1627    ,       0.0418  ,       0.010721757     ,       3.259166406     ,       129.1993186     ,       0.42450407      ,       0
DATA    0.7826  ,       17.6521 ,       0.8225  ,       5630    ,       0.0448  ,       0.010983264     ,       1.110470147     ,       37.20977507     ,       1.029587786     ,       0.003298422
DATA    1.0000  ,       0.0000  ,       0.8493  ,       681     ,       0.0675  ,       0.013075314     ,       0.292302696     ,       0       ,       0.701464423     ,       0.108533659
DATA    1.0000  ,       0.0000  ,       0.7757  ,       1225    ,       0.0865  ,       0.01124477      ,       1.458738538     ,       7.281589914     ,       0.198211948     ,       0.019031428
DATA    0.6289  ,       11.3382 ,       0.7628  ,       1555    ,       0.0656  ,       0.010983264     ,       1.945372372     ,       96.78173669     ,       0.373737253     ,       0.012896037
DATA    0.7497  ,       9.3899  ,       0.6975  ,       5896    ,       0.0205  ,       0.011506276     ,       1.418665309     ,       0.192085132     ,       0.312091519     ,       0.017404514
DATA    0.4033  ,       10.5963 ,       0.7715  ,       4872    ,       0.0509  ,       0.012813808     ,       0.44105854      ,       3.637838834     ,       0.49098426      ,       0.170559669
DATA    1.0000  ,       0.0000  ,       0.7597  ,       953     ,       0.0409  ,       0.010721757     ,       8.43731432      ,       0       ,       0.017467054     ,       0.003053596
DATA    0.4632  ,       36.3267 ,       0.8129  ,       5335    ,       0.0244  ,       0.012813808     ,       3.234398782     ,       33.54304115     ,       0.368067018     ,       0.094575466
DATA    0.1969  ,       50.1234 ,       0.7554  ,       5059    ,       0.0168  ,       0.012552301     ,       1.233654083     ,       0.85619004      ,       0.222593571     ,       0.018275376
DATA    0.1107  ,       294.7680        ,       0.7573  ,       149125  ,       0.0103  ,       0.011506276     ,       2.004800853     ,       75.78508313     ,       0.744131117     ,       0.029912018
DATA    0.5964  ,       14.8706 ,       0.8201  ,       3645    ,       0.0228  ,       0.010721757     ,       2.092600081     ,       29.47396401     ,       0.364158855     ,       0.053300529
DATA    0.4295  ,       9.5265  ,       0.7703  ,       2342    ,       0.0640  ,       0.011506276     ,       1.098117513     ,       1.381780546     ,       0.408388221     ,       0.026129199
DATA    1.0000  ,       0.0000  ,       0.8776  ,       172     ,       0.0465  ,       0.012813808     ,       0.349912522     ,       0       ,       0.386182431     ,       0.041083087
DATA    1.0000  ,       0.0000  ,       0.7428  ,       817     ,       0.0514  ,       0.012813808     ,       0.475030451     ,       1.769992196     ,       0.193626285     ,       0.156161584
DATA    0.1417  ,       110.5589        ,       0.8045  ,       10394   ,       0.0203  ,       0.010983264     ,       0.458545049     ,       1.194394309     ,       0.144996483     ,       0.015603435
DATA    1.0000  ,       0.0000  ,       0.7782  ,       567     ,       0.0459  ,       0.012290795     ,       0.528317836     ,       29.93702091     ,       0.192835499     ,       0
DATA    0.5301  ,       10.8522 ,       0.8604  ,       1477    ,       0.0183  ,       0.011506276     ,       0       ,       1.77383592      ,       0.331088445     ,       0
DATA    1.0000  ,       0.0000  ,       0.7844  ,       458     ,       0.0371  ,       0.012552301     ,       0.36963321      ,       35.80393711     ,       0.358795746     ,       0
DATA    1.0000  ,       0.0000  ,       0.6260  ,       1208    ,       0.0522  ,       0.012552301     ,       1.017068038     ,       1.802027954     ,       0.84098986      ,       0.01373486
DATA    0.1028  ,       83.8269 ,       0.8420  ,       2461    ,       0.0110  ,       0.011506276     ,       0       ,       25.00452981     ,       0.280190064     ,       0.050977501
DATA    0.3674  ,       85.6793 ,       0.8014  ,       8304    ,       0.0170  ,       0.011767782     ,       1.500570869     ,       4.568667625     ,       1.198578407     ,       0.047773768
DATA    0.2909  ,       76.8441 ,       0.7532  ,       37889   ,       0.0164  ,       0.012290795     ,       1.401481566     ,       0.492518237     ,       1.126052341     ,       0.047641968
DATA    0.4383  ,       42.0699 ,       0.7663  ,       16704   ,       0.0330  ,       0.01124477      ,       1.394556298     ,       61.77288793     ,       0.88442138      ,       0.005098776
DATA    0.3278  ,       95.9345 ,       0.8130  ,       5406    ,       0.0194  ,       0.01124477      ,       4.540654699     ,       139.0602779     ,       0.921407082     ,       0
DATA    0.3203  ,       74.2411 ,       0.7856  ,       7773    ,       0.0277  ,       0.012029289     ,       2.529510961     ,       95.03157742     ,       0.432568678     ,       0.049547539
DATA    0.3969  ,       38.8989 ,       0.7636  ,       3585    ,       0.0226  ,       0.012552301     ,       3.634400864     ,       0       ,       0.348147764     ,       0.01699913
DATA    0.2239  ,       59.1427 ,       0.7508  ,       15254   ,       0.0307  ,       0.01124477      ,       2.183253397     ,       94.37507846     ,       0.412016545     ,       0.034733701
DATA    0.3715  ,       23.7780 ,       0.7287  ,       3483    ,       0.0339  ,       0.011506276     ,       3.649793613     ,       11.12018074     ,       0.826669218     ,       0.092281904
DATA    1.0000  ,       0.0000  ,       0.7684  ,       428     ,       0.0234  ,       0.012552301     ,       0.888148765     ,       19.92497386     ,       0.166089416     ,       0
DATA    0.5556  ,       14.7124 ,       0.7293  ,       1341    ,       0.0194  ,       0.011506276     ,       0.76524315      ,       0       ,       0.207819709     ,       0.004751765
DATA    0.3833  ,       35.0842 ,       0.7530  ,       4527    ,       0.0186  ,       0.009414226     ,       0.301583312     ,       2.299021858     ,       0.937905846     ,       0.036789118
DATA    0.4358  ,       12.5046 ,       0.8207  ,       1822    ,       0.0505  ,       0.009414226     ,       1.423184527     ,       1.979867066     ,       0.702822596     ,       0.077568149
DATA    1.0000  ,       0.0000  ,       0.8452  ,       1508    ,       0.0186  ,       0.00915272      ,       0.4199916       ,       128.5745581     ,       0.274257705     ,       0
DATA    0.3935  ,       50.6677 ,       0.8041  ,       11073   ,       0.0190  ,       0.00915272      ,       1.772915881     ,       0       ,       0.456369503     ,       0.03970461
DATA    0.4755  ,       34.5046 ,       0.7694  ,       2696    ,       0.0115  ,       0.010460251     ,       0.854075159     ,       8.450619209     ,       0.4352587       ,       0.125833744
DATA    0.0694  ,       151.3876        ,       0.7176  ,       1700    ,       0.0094  ,       0.00915272      ,       0       ,       5.803899273     ,       0.29419314      ,       0
DATA    0.3961  ,       27.9813 ,       0.7860  ,       2378    ,       0.0189  ,       0.00915272      ,       0.662509743     ,       0       ,       0.227644795     ,       0.100842649
DATA    0.6825  ,       12.3115 ,       0.8236  ,       2649    ,       0.0434  ,       0.009414226     ,       2.532572098     ,       0.297094837     ,       0.195260701     ,       0.028741803
DATA    0.6967  ,       12.1311 ,       0.8246  ,       1830    ,       0.0694  ,       0.00915272      ,       1.857923497     ,       0       ,       0.73767299      ,       0
DATA    0.2419  ,       38.7013 ,       0.7935  ,       2162    ,       0.0254  ,       0.009414226     ,       0.354191263     ,       0.055287674     ,       0.145663274     ,       0.040407391
DATA    0.1700  ,       96.3429 ,       0.7823  ,       3047    ,       0.0289  ,       0.009414226     ,       1.333333333     ,       0       ,       0.066793581     ,       0
DATA    0.1037  ,       70.4632 ,       0.7951  ,       2699    ,       0.0193  ,       0.009414226     ,       2.068161957     ,       0.433922849     ,       0.374323855     ,       0.113191874
DATA    0.3766  ,       17.0521 ,       0.8042  ,       1904    ,       0.0184  ,       0.010460251     ,       0.732653354     ,       9.517455209     ,       0.59466213      ,       0.008487215
DATA    0.4709  ,       13.7346 ,       0.7914  ,       1682    ,       0.0559  ,       0.009675732     ,       1.49691358      ,       0.300095602     ,       0.206558161     ,       0.038562285
DATA    0.3261  ,       79.4602 ,       0.8158  ,       1791    ,       0.0140  ,       0.00915272      ,       0.526662278     ,       11.3960114      ,       0.350763416     ,       0
DATA    0.3660  ,       28.9567 ,       0.8157  ,       1795    ,       0.0201  ,       0.00915272      ,       0       ,       15.08688429     ,       0.37856046      ,       0
DATA    0.3412  ,       35.6469 ,       0.8242  ,       1606    ,       0.0274  ,       0.00915272      ,       0       ,       0       ,       0.442620571     ,       0.065295951
DATA    0.5424  ,       33.8619 ,       0.7579  ,       4620    ,       0.0232  ,       0.00915272      ,       0.480538203     ,       3.618835314     ,       1.480283258     ,       0
DATA    0.5821  ,       14.9010 ,       0.8417  ,       1747    ,       0.0309  ,       0.009414226     ,       1.796284956     ,       0       ,       0.171656304     ,       0.037108968
DATA    0.5277  ,       58.8351 ,       0.7629  ,       1262    ,       0.0103  ,       0.010460251     ,       4.343534057     ,       19.81386291     ,       0.450969181     ,       0.59468762
DATA    0.4835  ,       12.5171 ,       0.7962  ,       1241    ,       0.0451  ,       0.009414226     ,       0.898262058     ,       0       ,       0.474486922     ,       0.007207347
DATA    0.2363  ,       52.1593 ,       0.8017  ,       1629    ,       0.0270  ,       0.009414226     ,       3.186582809     ,       0.040214477     ,       0.161416555     ,       0.050911528
DATA    0.4417  ,       56.6360 ,       0.7635  ,       20070   ,       0.0156  ,       0.00915272      ,       0.146568281     ,       10.26382583     ,       0.409473499     ,       0.086533279
DATA    0.3080  ,       50.9568 ,       0.7380  ,       20705   ,       0.0255  ,       0.009675732     ,       1.685872813     ,       40.81055958     ,       0.141293809     ,       0.056891616
DATA    0.5057  ,       33.1867 ,       0.7263  ,       1831    ,       0.0257  ,       0.00915272      ,       0.806747341     ,       0       ,       0.61443719      ,       0.057252689
DATA    1.0000  ,       0.0000  ,       0.8137  ,       579     ,       0.0415  ,       0.009414226     ,       1.328653798     ,       0       ,       0.389189639     ,       0.161906001
DATA    0.1129  ,       92.9789 ,       0.9144  ,       1045    ,       0.0124  ,       0.00915272      ,       0       ,       51.81270448     ,       0.159075365     ,       0
DATA    1.0000  ,       0.0000  ,       0.8264  ,       267     ,       0.0187  ,       0.010460251     ,       0       ,       0       ,       0.076027013     ,       0
DATA    0.1691  ,       108.8626        ,       0.7263  ,       1774    ,       0.0265  ,       0.009414226     ,       1.329394387     ,       0       ,       0.467279528     ,       0
DATA    0.2956  ,       115.1922        ,       0.7301  ,       4510    ,       0.0122  ,       0.00915272      ,       1.160261059     ,       0.03248388      ,       0.870310275     ,       0.14715739
DATA    0.5965  ,       5.4838  ,       0.7839  ,       2295    ,       0.0675  ,       0.00915272      ,       1.101504205     ,       1.750630227     ,       0.500159307     ,       0.369200412
DATA    0.5591  ,       27.2625 ,       0.7845  ,       4414    ,       0.0136  ,       0.009414226     ,       0.826562062     ,       4.373278022     ,       0.488459388     ,       0.002611472
DATA    0.0968  ,       447.6121        ,       0.7370  ,       105018  ,       0.0045  ,       0.00915272      ,       0.297310052     ,       4.22529746      ,       6.415647972     ,       0.010683966


FOR h = 1 TO popa
FOR j = 1 TO c
READ ap(h, j)
PRINT ap(h, j);
ap(h, j) = -ap(h, j)
IF j = 2 THEN ap(h, j) = -ap(h, j)
IF j = 3 THEN ap(h, j) = -ap(h, j)
IF j = 4 THEN ap(h, j) = -ap(h, j)
IF j = 8 THEN ap(h, j) = -ap(h, j)
IF j = 9 THEN ap(h, j) = -ap(h, j)

NEXT j
PRINT
NEXT h

FOR h = 1 TO popa
PRINT h
rem cr = 0: score = 0: scoret = 0: scoref = 0
FOR ra = 1 TO rp
FOR j = 1 TO c
IF ruleb(ra, j) = 1000 THEN GOTO 100050
IF ap(h, j) < ruleb(ra, j) THEN GOTO 100100
100050 NEXT j
IF credrulb(ra) > cr THEN cr = credrulb(ra)
score = score + 1
scoref = scoref + credrulb(ra)
IF credrulb(ra) = 1 THEN scoret = scoret + 1

WRITE #1, "comune", h, "regola", ra
PRINT "comune", h, "regola", ra
100100 NEXT ra
crd(h) = cr
scored(h) = score: score=0
scorefd(h) = scoref: scoref=0
scoretd(h) = scoret: scoref=0

WRITE #1, "comune", h, "credibilit…", cr
NEXT h

WRITE #1, "cred"
FOR h = 1 TO popa
WRITE #1, crd(h)
NEXT h

WRITE #1, "score"
FOR h = 1 TO popa
WRITE #1, scored(h)
NEXT h

WRITE #1, "scoref"
FOR h = 1 TO popa
WRITE #1, scorefd(h)
NEXT h

WRITE #1, "scoret"
FOR h = 1 TO popa
WRITE #1, scoretd(h)
NEXT h

CLOSE
END

---

### Post by wmcbrine on 2010-02-05
Ugh, I have a headache just from skimming that. Mixing numbered and unnumbered lines... I've never seen that before. Is that legal?

What is the program meant to do?

---

### Post by geonomica on 2010-02-06
right!
I've tried to convert code with my little qbasic knowledge without significant result. I've tried with bcc converter, but even this refused to work with that code. I'm desperate.
The code implemente a multicriteria decision making but I don't know the exact algorithm. 
HELP

---

### Post by Gadgetech on 2010-02-06
It's been about 15 years since I touched anything in QBASIC. I do remember that QBASIC only requires line numbers for lines that you want to reference with a GOTO statement, etc. You can get rid of all of the REM lines. REM stands for Remark. It's a comment.

It looks like a bunch of fun with arrays and FOR-NEXT loops.

The main body of the program is all before the **6030 END** line. Everything after that is basically subroutines. I guess in C you would make these different functions? Sorry, I've only read about 2 pages of a C book.

Makes me think of those long nights spent in the robotics lab back in school.

---

### Post by geonomica on 2010-02-06
Thanks, 
indeed my difficulty is find sub routine in QBASIC. I cant find START and END sub routine because of the huge amount of GOTO LABEL
by

---

### Post by nvteighen on 2010-02-06
This is ridiculously bad written... QBASIC had support for structured programming (SUBs and FUNCTIONs). Can you contact the creator? I guess it will save you time.

Another idea would be a reimplmentation in C rather than a strict translation. If it does exactly the same (or better), no matter what algorithm is used, nobody will care whether it was a translation or a reimplementation.

---

### Post by geonomica on 2010-02-06
unfortunatly the author isn't interested to rewrite, or simply explain, the code. He built code some year ago and now He's employed in other field.
Now I'm trying to rewrite the code in C but  my BASIC knowledge is quite low. Mi difficult is understand exactly the code from 8000 to 12380. It seem a big cicle with  plenty of "IF" "THEN", and, GOTO.
geo

---

### Post by CptPicard on 2010-02-06
Well, C allows for labels and gotos too, although in proper C, their use is almost banned. The section you're referring to doesn't seem that hard to write into C that makes use of them.

---

### Post by Zugzwang on 2010-02-06
I've got a suggestion:

There's this qb2c converter that might be of help. Having a quick look at its README file, the only thing that it doesn't seem to support are these "DATA" and "READ" lines. If that's really all, you might be better off rewriting the program a little bit in order not to use these commands (you can put the data into a file and read from there) and use the converter instead.

---

### Post by underquark on 2010-02-06
I use DosBox to run some old games.  I believe QBasic ought to run in DosBox as well so might be worth trying running the program directly.

---

### Post by wmcbrine on 2010-02-06
> **geonomica said:**
> The code implemente a multicriteria decision makingMore detail, please. If you expect us to help you, you can't be coy about what this is all for.

Can you post an attachment with the actual working program file? The formatting is a bit screwed up in your post.

---

### Post by nvteighen on 2010-02-06
> **underquark said:**
> I use DosBox to run some old games.  I believe QBasic ought to run in DosBox as well so might be worth trying running the program directly.

It does run pretty well. Even QuickBASIC 4.5 does.

---

### Post by underquark on 2010-02-06
I just found and downloaded a Windows version of qb64, ran it in Windows XP in VirtualBox and the program runs.  Generates columns of figures like:

```

comune  91 regola 38
 92
comune 92 regola 1
comune 92 regola 2
```
No idea what it means but if that's what it's meant to churn out then give running it this way a try.

---

### Post by underquark on 2010-02-06
Say, this isn't an Italian Football results predictor or something?  Wow, I'm going to be rich.

---

### Post by nikhilbhardwaj on 2010-02-06
> **underquark said:**
> Say, this isn't an Italian Football results predictor or something?  Wow, I'm going to be rich.
you wish :D

i'd also suggest a rewrite
no point going on translating
its not too long as it is

---

### Post by geonomica on 2010-02-07
well,
I'm studing QBASIC,:confused: so I think I'll try to define the exact algorithm and rewrite it in C.

P.S. No, I'm apologize but the code isn't Italian Football results predictor

Thanks

geo

---

### Post by nvteighen on 2010-02-07
> **geonomica said:**
> 
P.S. No, I'm apologize but the code isn't Italian Football results predictor


No need for a predictor. All matches end up 1-1, 1-0, 0-1, and very occasionally 2-1 or 1-2 due to [Catenaccio]("http://en.wikipedia.org/wiki/Catenaccio") :p

---

### Post by CptPicard on 2010-02-07
> **nvteighen said:**
> No need for a predictor. All matches end up 1-1, 1-0, 0-1, and very occasionally 2-1 or 1-2 due to [Catenaccio]("http://en.wikipedia.org/wiki/Catenaccio") :p

Coming from someone who actually makes money on this stuff, it's a known quantity that everything up to 2-1 either way tends to be unprofitable also because they are commonly played by the punters... not big enough odds there to cover your investment in the long run.

---

### Post by raydeen on 2010-02-08
Ya know, I'd always heard of spaghetti code. Never thought I'd ever see such a fine example of it though. Even in my glory days writing BASIC on my Atari 400, I never had code that badly written. Just wow.

---

