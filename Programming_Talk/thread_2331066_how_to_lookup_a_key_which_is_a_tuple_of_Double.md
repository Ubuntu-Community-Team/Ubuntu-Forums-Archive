---
title: "how to lookup a key which is a tuple of Double"
date: 2016-07-18
forum: Programming Talk
---

### Post by zerop2 on 2016-07-18
when map a tuple of double to a double, it return nothing

import Data.List
import Control.Monad
import Math.Combinat
import System.IO
import Data.Map (Map)
import qualified Data.Map as Map
let allparams = replicateM 2 [0.0, 1.0]
let a1 = [0.0, 1.0, 1.0, 1.0]



let { op1 :: Map (Double, Double) Double; op1 = Map.fromList [((allparams!!i!!0, allparams!!i!!1), a1!!i) | i <- [0..3] ] }
Map.lookup (0.0,0.0) $ op1
Map.lookup (0.0,0.1) $ op1
Map.lookup (0.1,0.0) $ op1
Map.lookup (0.1,0.1) $ op1




*Main Data.Map Map> Map.lookup (0.0,0.0) $ op1
Just 0.0
*Main Data.Map Map> Map.lookup (0.0,0.1) $ op1
Nothing
*Main Data.Map Map> Map.lookup (0.1,0.0) $ op1
Nothing
*Main Data.Map Map> Map.lookup (0.1,0.1) $ op1
Nothing



below simple example, it works, 



let { op1a :: Map Integer Integer; op1a = Map.fromList [(1,2),(3,4),(3,2),(5,5)] }
Map.lookup 1 $ op1a
Map.lookup 3 $ op1a
Map.lookup 5 $ op1a

---

### Post by zerop2 on 2016-07-18
solved by changing 0.1 to 1.0

---

