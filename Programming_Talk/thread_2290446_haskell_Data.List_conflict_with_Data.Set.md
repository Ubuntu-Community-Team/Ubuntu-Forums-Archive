---
title: "haskell Data.List conflict with Data.Set"
date: 2015-08-12
forum: Programming Talk
---

### Post by zerop2 on 2015-08-12
Prelude> :l trees.hs
[1 of 1] Compiling Main             ( trees.hs, interpreted )


trees.hs:45:16:
    Ambiguous occurrence `null'
    It could refer to either `Data.List.null',
                             imported from `Data.List' at trees.hs:1:1-16
                             (and originally defined in `GHC.List')
                          or `Data.Set.null',
                             imported from `Data.Set' at trees.hs:3:1-15
                             (and originally defined in `containers-0.5.0.0:Data.Set.Base')


trees.hs:45:35:
    Ambiguous occurrence `null'
    It could refer to either `Data.List.null',
                             imported from `Data.List' at trees.hs:1:1-16
                             (and originally defined in `GHC.List')
                          or `Data.Set.null',
                             imported from `Data.Set' at trees.hs:3:1-15
                             (and originally defined in `containers-0.5.0.0:Data.Set.Base')


trees.hs:60:13:
    Ambiguous occurrence `map'
    It could refer to either `Data.List.map',
                             imported from `Data.List' at trees.hs:1:1-16
                             (and originally defined in `GHC.Base')
                          or `Data.Set.map',
                             imported from `Data.Set' at trees.hs:3:1-15
                             (and originally defined in `containers-0.5.0.0:Data.Set.Base')


trees.hs:63:25:
    Ambiguous occurrence `map'
    It could refer to either `Data.List.map',
                             imported from `Data.List' at trees.hs:1:1-16
                             (and originally defined in `GHC.Base')
                          or `Data.Set.map',
                             imported from `Data.Set' at trees.hs:3:1-15
                             (and originally defined in `containers-0.5.0.0:Data.Set.Base')



import Data.List
import Data.Array
import Data.Set
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
--distsTo :: Vertex -> Graph Float -> Table Float
--distsTo v gr = foldGAll infinite distance gr 
--    where infinite = 10000000 -- well, you get the idea
--          distance v' neighbours 
--              | v == v' = 0
--              | otherwise = minimum [distV+arcWeight | (distV, arcWeight) <- neighbours]


type Automaton t = (Vertex, Graph t, Set Vertex) -- ^ Initial, transitions,fin


automatonToGraphviz (i, gr, fs) = showGraphViz (LabGraph gr lab)
    where lab :: Labeling String
          lab v = (if v == i then (">"++) else id) $ 
                  (if v `Set.member` fs then (++"|") else id) []

---

