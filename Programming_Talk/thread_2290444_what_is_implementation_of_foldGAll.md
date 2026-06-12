---
title: "what is implementation of foldGAll"
date: 2015-08-12
forum: Programming Talk
---

### Post by zerop2 on 2015-08-12
[https://wiki.haskell.org/The_Monad.Reader/Issue5/Practical_Graph_Handling#foldG](https://wiki.haskell.org/The_Monad.Reader/Issue5/Practical_Graph_Handling#foldG)
i follow 1.5.2

Prelude> :l trees.hs
[1 of 1] Compiling Main             ( trees.hs, interpreted )


trees.hs:39:22: parse error on input `='
Failed, modules loaded: none.



import Data.List
import Data.Array
--import Data.Graph 
import Control.Monad
import Math.Combinat
import Math.Core.Utils
import Math.Core.Field
import Math.Algebras.VectorSpace
import Math.Algebras.Structures
--import Math.CommutativeAlgebra.GroebnerBasis
--import Math.CommutativeAlgebra.Polynomial
--import Math.Algebras.Matrix
import System.IO
import qualified Data.Map as M


type Vertex = Int
type Table a = Array Vertex a
type Graph e = Table [(e, Vertex)]
type Bounds  = (Vertex, Vertex)
type Edge e = (Vertex, e, Vertex)


type Labeling a = Vertex -> a
data LabGraph n e = LabGraph (Graph e) (Labeling n)


foldGAll :: (Eq r) => r -> (Vertex -> [(e, r)] -> r) -> Graph e -> Table r
foldGAll i f g v = finalTbl
  where finalTbl = fixedPoint updateTbl initialTbl
          initialTbl = listArray bnds (replicate (rangeSize bnds) bot)
 
          fixedPoint f x = fp x
              where fp z = if z == z' then z else fp z'
                        where z' = f z
          updateTbl tbl = listArray bnds $ map recompute $ indices gr
              where recompute v = f v [(b, tbl!k) | (b, k) <- gr!v]
          bnds = bounds gr


foldG :: (Eq r) => r -> (Vertex -> [(e, r)] -> r) -> Graph e -> Vertex -> r
foldG i f g v = foldGAll i f g ! v


-- | Build a graph from a list of edges.
buildG :: Bounds -> [Edge e] -> Graph e
buildG bounds0 edges0 = accumArray (flip (:)) [] bounds0 [(v, (l,w)) | (v,l,w) <- edges0]
 
-- | The graph obtained by reversing all edges.
transposeG  :: Graph e -> Graph e
transposeG g = buildG (bounds g) (reverseE g)


edges :: Graph e -> [Edge e]
edges g = [ (v, l, w) | v <- indices g, (l, w) <- g!v ]
 
reverseE    :: Graph e -> [Edge e]
reverseE g   = [ (w, l, v) | (v, l, w) <- edges g ]


showGraphViz (LabGraph gr lab)  = 
    "digraph name {\n" ++
    "rankdir=LR;\n" ++
    (concatMap showNode $ indices gr) ++
    (concatMap showEdge $ edges gr) ++
    "}\n"
    where showEdge (from, t, to) = show from ++ " -> " ++ show to ++
				   " [label = \"" ++ show t ++ "\"];\n"
          showNode v = show v ++ " [label = " ++ (show $ lab v) ++ "];\n"
 


-- | Compute the distance to v for every vertex of gr.
distsTo :: Vertex -> Graph Float -> Table Float
distsTo v gr = foldGAll infinite distance gr 
    where infinite = 10000000 -- well, you get the idea
          distance v' neighbours 
              | v == v' = 0
              | otherwise = minimum [distV+arcWeight | (distV, arcWeight) <- neighbours]

---

