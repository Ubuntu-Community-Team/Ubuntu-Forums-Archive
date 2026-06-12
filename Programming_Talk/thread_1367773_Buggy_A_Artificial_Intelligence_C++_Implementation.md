---
title: "Buggy A* Artificial Intelligence C++ Implementation"
date: 2009-12-29
forum: Programming Talk
---

### Post by kiplingw on 2009-12-29
Greetings,

I am trying to implement the A* path finding algorithm in C++ as a template for an abstract base class. A user derives from an AStarBase template and implements pure virtual overrides to enable context specific heuristics (e.g. h(x)).

For my driver, I am using OpenGL / Freeglut to render the path and use the algorithm in a spatial sense. The green and red spheres represent the start and end goal locations respectively. The raised blocks represent obstacles the agent cannot pass through. The agent can move up, down, left, right, and diagonal - when block obstructions permit.

The algorithm works most of the time, but I notice in some scenarios it makes some weird jagged turns at the start, like in these two scenarios:

[IMG]http://www.thevertigo.com/temp/screens/ok-but-jagged.png[/IMG]

[IMG]http://www.thevertigo.com/temp/screens/also-ok-but-jagged.png[/IMG]

Note that it finds its way to the goal, but takes a weird route in both pics in the first few moves.

In this scenario, a solution is clearly available, but it doesn't find it. A* is difficult to debug because there are many states to keep track of and a lot of data to juggle.

[IMG]http://www.thevertigo.com/temp/screens/not-ok.png[/IMG]

I am confident my GL rendering code is rendering the path it is given correctly and have confirmed this by examining the solution vector manually. The problem is in AStarBase or in the PathFinder derived class.

AStarBase.h
```

/*
  Name:         AStarBase.h
  Author:       Kip Warner (kip@thevertigo.com)
  Description:  The A* search strategy algorithm. See Computational 
                Intelligence: A Logical Approach (Poole et al., 1998) for an
                explanation on the algorithm. Problem here is represented as a
                pattern for an abstract base class where h(x) is implemented via
                an override...
  License:      Copyright (C) 2009 Kip Warner
                Released under the terms of the GNU Public License V3.
*/

// Multiple include protection...
#ifndef _ASTARBASE_H_
#define _ASTARBASE_H_

// Includes...
#include <set>
#include <vector>
#include <algorithm>

// Namespace AI...
namespace Ai { namespace SearchStrategy {

    // Template helper macros for non-inline method implementation...

        // Template declaration argument list...
        #define AStarBaseTemplateDeclaration                                        \
                                                                                    \
            /* Type of intelligent agent */                                         \
            class   Agent_t,                                                        \
                                                                                    \
            /* The type of state each node represents */                            \
            class   State_t,                                                        \
                                                                                    \
            /* Type to use to represent arc costs... */                             \
            class   Cost_t
        
        // Template method definition argument list...
        #define AStarBaseTemplateArgumentList                                       \
            Agent_t,                                                                \
            State_t,                                                                \
            Cost_t

    // The A* search strategy pattern abstract base class...
    template<AStarBaseTemplateDeclaration>
    class AStarBase
    {
        // Public data types...
        public:

            // A node class encapsulating a state in the solution space...
            class Node
            {
                // Public methods...
                public:

                    // Constructor...
                    Node(State_t const &_State)
                        : m_State(_State),
                          m_CostFromStart(0),
                          m_CostToGoal(0),
                          m_pParentNode(NULL) { }

                    // Get cost of cheapest path that led to this state from start...
                    inline Cost_t GetCostFromStart() const { return m_CostFromStart; }

                    // Get the state...
                    inline State_t const &GetState() const { return m_State; }

                    // Less than operator...
                    inline bool operator<(Node const &RightSide) const
                    {
                        // Perform comparison...
                        return (GetTotalCost() < RightSide.GetTotalCost());
                    }

                    // Assignment operator...
                    inline Node &operator=(Node const &RightSide)
                    {
                        // Self assignment, skip...
                        if(this == &RightSide)
                            return *this;
                        
                        // Initialize from right side...
                        m_State         = RightSide.m_State;
                        m_CostFromStart = RightSide.m_CostFromStart;
                        m_CostToGoal    = RightSide.m_CostToGoal;
                        m_pParentNode   = RightSide.m_pParentNode;
                        
                        // Return reference to ourself...
                        return *this;
                    }

                    // Total cost is sum of cost from start to this state and the
                    //  underestimate from this state to the goal...
                    inline Cost_t GetTotalCost() const { return m_CostFromStart + m_CostToGoal; }
                    
                    // Get the parent node, or NULL if none...
                    inline Node const *GetParent() const { return m_pParentNode; }

                    // Set the cost from start to this node...
                    inline void SetCostFromStart(Cost_t const &NewCostFromStart) { m_CostFromStart = NewCostFromStart; }

                    // Set the cost to goal from this node...
                    inline void SetCostToGoal(Cost_t const &NewCostToGoal) { m_CostToGoal = NewCostToGoal; }

                    // Set the parent node...
                    inline void SetParent(Node const *pParent) { m_pParentNode = pParent; }
                    
                // Private data...
                private:

                    // A user's state...
                    State_t         m_State;

                    // Cost of cheapest path that led to this state from start...
                    Cost_t          m_CostFromStart;

                    // Underestimate heuristic value of cost to travel From to Goal...
                    Cost_t          m_CostToGoal;

                    // Parent's state...
                    Node const     *m_pParentNode;
            };

        // Public methods...
        public:

            // Constructor...
            AStarBase();
            
            // Perform the search...
            bool Search(Agent_t const &Agent, State_t const &Start, State_t const &Goal);

            // Retrieve the optimal list of states from start to goal...
            std::vector<State_t> const &Solution() const;
            
            // Deconstructor...
            virtual ~AStarBase() 
            {
            }

        // Private data types...
        private:
        
            // Binary predicate used for enforcing strict weak ordering on 
            //  states. Want states arranged from lowest total cost to greatest...
            class NodeLessThanComparable
            {
                // Public methods...
                public:

                    // Functor callback...
                    bool operator()(Node const &First, Node const &Second) const
                    {
                        // If the first element is not less than second, and the
                        //  second is not less than the first, std::set's logic
                        //  is they are equivalent. We take advantage of this
                        //  for nodes with same state...
                        if(First.GetState() == Second.GetState())
                            return false;
                        
                        // Otherwise sort by total cost...
                        else
                            return (First.GetTotalCost() < Second.GetTotalCost());
                    }
            };

            // Open list iterator...
            typedef typename std::set<Node, NodeLessThanComparable>::iterator
                OpenListIterator;

            // Closed list iterator...
            typedef typename std::set<State_t>::iterator ClosedListIterator;

        // Private methods...
        private:

            // Determines cost of traversal from state to neighbour...
            virtual Cost_t CostToNeighbour(
                Agent_t const &Agent,
                State_t const &From, 
                State_t const &Neighbour) const = 0;

            // An underestimate heuristic of the cost to travel From to Goal via
            //  agent. e.g. Manhattan distance for path finding applications. This
            //  is typically referred to as h(x) in the literature...
            virtual Cost_t CostToGoalHeuristic(
                Agent_t const &Agent,
                State_t const &From, 
                State_t const &Goal) const = 0;

            // Get the state's neighbours. Caller frees...
            virtual State_t const * GetNeighbours(
                State_t const &State, 
                size_t &Total) const = 0;

            // Reset the object for a new search...
            void Reset();

        // Private data...
        private:
            
            // The optimal list of states from start to goal...
            std::vector<State_t>    m_SolutionStateList;
    };
    
    // The actual template definitions imported because no export keyword yet...
    #include "AStarBase.cpp"
}}

#endif

```

AStarBase.cpp
```

/*
  Name:         AStarBase.cpp
  Author:       Kip Warner (kip@thevertigo.com)
  Description:  The A* search strategy algorithm. See Computational 
                Intelligence: A Logical Approach (Poole et al., 1998) for an
                explanation on the algorithm. Problem here is represented as a
                pattern for an abstract base class where h(x) is implemented via
                an override...
  License:      Copyright (C) 2009 Kip Warner
                Released under the terms of the GNU Public License V3.
*/

// Constructor...
template<AStarBaseTemplateDeclaration>
AStarBase<AStarBaseTemplateArgumentList>::AStarBase()
{

}

// Reset the object for a new search...
template<AStarBaseTemplateDeclaration>
void AStarBase<AStarBaseTemplateArgumentList>::Reset()
{
    // Clear the solution state list if requested...
    m_SolutionStateList.clear();
}

// Perform the search...
template<AStarBaseTemplateDeclaration>
bool AStarBase<AStarBaseTemplateArgumentList>::Search(
    Agent_t const &Agent, State_t const &Start, State_t const &Goal)
{
    // Open list for unexamined states...
    std::set<Node, NodeLessThanComparable>  OpenList;

    // Closed list for examined states...
    std::set<State_t>                       ClosedList;

    // Interesting nodes we 
    std::vector<Node const *>               InterestingNodes;

    // Clear any existing solution...
    Reset();

    // Initialize the start node...
    Node StartNode(Start);
    StartNode.SetCostToGoal(
        CostToGoalHeuristic(Agent, Start, Goal));

    // We begin with the start node in the open list...
    OpenList.insert(StartNode);

    // Keep expanding and examining the frontier until success or failure...
    while(!OpenList.empty())
    {
        // Get the node with the lowest total cost from the open list...
        OpenListIterator CurrentPos = OpenList.begin();
        Node CurrentNode = *CurrentPos;

        // Remove it from the open list. Also amortized constant time...
        OpenList.erase(CurrentPos);
        
        // We've reached the goal...
        if(CurrentNode.GetState() == Goal)
        {
            // Construct path backwards from current node (goal) to start...
            for(Node const *pSolutionNode = &CurrentNode; 
                pSolutionNode->GetParent();
                pSolutionNode = pSolutionNode->GetParent())
                m_SolutionStateList.push_back(pSolutionNode->GetState());

            // For user's convenience, begin with the starting node...
            m_SolutionStateList.push_back(Start);

            // Reverse all of it so state list begins with start and ends with goal...
          ::std::reverse(m_SolutionStateList.begin(), m_SolutionStateList.end());

            // Cleanup...
            
                // Interesting nodes list no longer needed, since we just wanted
                //  the states they contained...
                while(!InterestingNodes.empty())
                {
                    // Deallocate...
                    delete InterestingNodes.back();
                    
                    // Remove dead pointer...
                    InterestingNodes.pop_back();
                }

                // Shrink the solution state list to fit just what it needs...
                if(m_SolutionStateList.capacity() > m_SolutionStateList.size())
                    m_SolutionStateList.resize(m_SolutionStateList.size());

            // Done...
            return true;
        }

        // Haven't reached goal yet...
        else
        {
            // Variables...
            size_t Total = 0;

            // Get all of this state's neighbours... (directed arcs to them)
            State_t const * const pNeighbourStates = GetNeighbours(CurrentNode.GetState(), Total);

            // Examine each of its neighbours...
            for(unsigned int NeighbourIndex = 0; NeighbourIndex < Total; ++NeighbourIndex)
            {
                // Create the new node from state's neighbour...
                Node NeighbourNode = pNeighbourStates[NeighbourIndex];

                // Search for node in both open and closed lists in logarithmic 
                //  time and get reference so we can possibly update it...
                
                    // Closed list...
                    ClosedListIterator ClosedCheck = ClosedList.find(NeighbourNode.GetState());

                    // Open list...
                    OpenListIterator OpenCheck = OpenList.find(NeighbourNode);

                    // If we know of it already, use what we know...
                    if(OpenCheck != OpenList.end())
                        NeighbourNode = *OpenCheck;

                // What is the cost from current state to this neighbour?
                Cost_t const CostFromStartToNeighbour = 
                    CurrentNode.GetCostFromStart() + 
                    CostToNeighbour(Agent, CurrentNode.GetState(), NeighbourNode.GetState());

                // Ignore this state if already investigated and no improvement...
                if((ClosedCheck != ClosedList.end() || OpenCheck != OpenList.end()) &&
                   (NeighbourNode.GetCostFromStart() <= CostFromStartToNeighbour))
                    continue;

                // Store the new or improved version...
                else
                {
                    // The node needs to be persistent so we can unchain 
                    //  the solution, if any, later...
                    Node const *SavedNode = new Node(CurrentNode);
                    InterestingNodes.push_back(SavedNode);
                    
                    // Link the node back up to a better parent...
                    NeighbourNode.SetParent(SavedNode);
                    NeighbourNode.SetCostFromStart(CostFromStartToNeighbour);
                    NeighbourNode.SetCostToGoal(
                        CostToGoalHeuristic(Agent, NeighbourNode.GetState(), Goal));
                    
                    // If it's in the closed list, remove it. If using iterator,
                    //  this happens in amortized constant time...
                    if(ClosedCheck != ClosedList.end())
                        ClosedList.erase(ClosedCheck);
                    
                    // If it's in the open list, update it...
                    if(OpenCheck != OpenList.end())
                    {
                        OpenList.erase(OpenCheck);
                        OpenList.insert(NeighbourNode);
                    }

                    // Otherwise, insert into frontier...
                    else
                        OpenList.insert(NeighbourNode);
                }
            }
            
            // Cleanup the neighbours...
            delete [] pNeighbourStates;
        }

        // Done examining the current node, remember with closed list...
        ClosedList.insert(CurrentNode.GetState());
    }

    // The open list is empty, so nothing left to examine...

        // Cleanup...

            // Interesting nodes list no longer needed, since we just wanted
            //  the states they contained...
            while(!InterestingNodes.empty())
            {
                // Deallocate...
                delete InterestingNodes.back();
                    
                // Remove dead pointer...
                InterestingNodes.pop_back();
            }

        // Inform caller search for solution failed...
        return false;
}

// Retrieve the optimal list of nodes from start to goal...
template<AStarBaseTemplateDeclaration>
std::vector<State_t> const &AStarBase<AStarBaseTemplateArgumentList>::Solution() const
{ 
    // Return it...
    return m_SolutionStateList;
}

```

PathFinder.h
```

/*
  Name:         PathFinder.h
  Author:       Kip Warner (kip@thevertigo.com)
  Description:  The context specific subclass of the A* search strategy...
                algorithm. See Computational Intelligence: A Logical Approach 
                (Poole et al., 1998) for an explanation on the algorithm...
  License:      Copyright (C) 2009 Kip Warner
                Released under the terms of the GNU Public License V3.
*/

// Multiple include protection...
#ifndef _PATHFINDER_H_
#define _PATHFINDER_H_

// Includes...

    // Freeglut and OpenGL...
    #define GL_GLEXT_PROTOTYPES
    #include <GL/freeglut.h>

    // AI superset from which we are derived...
    #include "AStarBase.h"

// Checkerboard dimension...
#define CHECKERBOARD_DIMENSION 16

// The agent within the path finder world...
class PathAgent
{

};

// A state within the path finder solution space...
class PathState
{
    // Public methods...
    public:

        // Default constructor...
        PathState()
            : X(0), Y(0)
        {
        }
        
        // Constructor...
        PathState(unsigned int const _X, unsigned int const _Y)
            : X(_X), Y(_Y)
        {
        }
        
        // Accessors...
        inline unsigned int GetX() const { return X; }
        inline unsigned int GetY() const { return Y; }

        // Comparison operator needed for sorting...
        inline bool operator<(PathState const &RightSide) const
        {
            // Sort first by X coordinate...
            if(X < RightSide.X)
                return true;
            
            // If they are the same, sort by Y coordinate...
            else if(X == RightSide.X)
                return (Y < RightSide.Y);
            
            // Right side's X coordinate larger than ours...
            else
                return false;
        }

        // Assignment operator...
        inline PathState &operator=(PathState const &RightSide) { X = RightSide.GetX(); Y = RightSide.GetY(); return *this; }
        
        // Equivalence operator...
        bool operator==(PathState const &RightSide) const { return ((X == RightSide.X) && (Y == RightSide.Y)); }

    // Protected data...
    protected:
    
        // The grid location of this state...
        unsigned int X, Y;
};

// The pathfinder class...
class PathFinder : public Ai::SearchStrategy::AStarBase<PathAgent, PathState, float>
{
    // Public methods...
    public:

        // Constructor...
        PathFinder();

        // Get a grid square...
        inline GLubyte const &GetGridSquare(GLuint const X, GLuint const Y) const { return Grid[Y][X]; }

        // Is a square ascended?
        inline bool IsAscended(GLuint const X, GLuint const Y) const { return (Grid[Y][X] != 0); }

        // Start square accessors and mutators...
        inline void DisableStartSquare() { StartSelected = false; }
        inline bool IsStartEnabled() const { return StartSelected; }
        inline GLuint GetStartX() const { return StartSquare[0]; }
        inline GLuint GetStartY() const { return StartSquare[1]; }
        
        // End square accessors and mutators...
        inline void DisableEndSquare() { EndSelected = false; }
        inline bool IsEndEnabled() const { return EndSelected; }
        inline GLuint GetEndX() const { return EndSquare[0]; }
        inline GLuint GetEndY() const { return EndSquare[1]; }

        // Set state of a grid square...
        inline void SetGridSquare(GLuint const X, GLuint const Y, GLubyte const Level) { Grid[Y][X] = Level; }
        
        // Set start grid square...
        inline void SetStartSquare(GLuint const X, GLuint const Y) { StartSelected = true; StartSquare[0] = X; StartSquare[1] = Y; }
        
        // Set end grid square...
        inline void SetEndSquare(GLuint const X, GLuint const Y) { EndSelected = true; EndSquare[0] = X; EndSquare[1] = Y; }

    // Protected methods...
    protected:

        // Determines cost of traversal from node to neighbour...
        float CostToNeighbour(
            PathAgent const &Agent, PathState const &From, PathState const &Neighbour) const;

        // An underestimate heuristic of the cost to travel From to Goal via
        //  agent. e.g. Manhattan distance for path finding applications. This
        //  is typically referred to as h(x) in the literature...
        float CostToGoalHeuristic(
            PathAgent const &Agent, PathState const &From, PathState const &Goal) const;
        
        // Get the state's neighbours. Caller frees...
        PathState const *GetNeighbours(PathState const &State, size_t &Total) const;

    // Protected data...
    protected:
    
        // Grid state...
        GLubyte Grid[CHECKERBOARD_DIMENSION][CHECKERBOARD_DIMENSION];
        
        // Start location...
        bool    StartSelected;
        GLuint  StartSquare[2];
        
        // Goal location...
        bool    EndSelected;
        GLuint  EndSquare[2];
};

#endif

```

PathFinder.cpp
```

/*
  Name:         PathFinder.cpp
  Author:       Kip Warner (kip@thevertigo.com)
  Description:  The context specific subclass of the A* search strategy...
                algorithm. See Computational Intelligence: A Logical Approach 
                (Poole et al., 1998) for an explanation on the algorithm...
  License:      Copyright (C) 2009 Kip Warner
                Released under the terms of the GNU Public License V3.
*/

// Includes

    // Declaration...
    #include "PathFinder.h"
    
    // Low level memory manipulation...
    #include <cstring>
    
    // Math stuff...
    #include <cmath>

    // Debugging stuff...
    #include <cassert>

// We are using things mostly within this name space...
using namespace Ai::SearchStrategy;

// Constructor...
PathFinder::PathFinder()
    : AStarBase<PathAgent, PathState, float>(),
      StartSelected(false),
      EndSelected(false)
{
    // Clear the grid state...
    memset(Grid, 0x00, sizeof(Grid));
}

// Determines cost of traversal from node to neighbour...
float PathFinder::CostToNeighbour(
    PathAgent const &Agent, PathState const &From, PathState const &Neighbour) const
{
    // For now, let's assume all neighbours cost the same...
    return 1.0f;
}

// An underestimate heuristic of the cost to travel From to Goal via
//  agent. e.g. Manhattan distance for path finding applications. This
//  is typically referred to as h(x) in the literature...
float PathFinder::CostToGoalHeuristic(
    PathAgent const &Agent, PathState const &From, PathState const &Goal) const
{
    // Compute Manhattan distance and multiply by cost of each square...
    return abs(From.GetX() - Goal.GetX()) + abs(From.GetY() - Goal.GetY()) * 1.0f;
}

// Get the state's neighbours. Caller frees...
PathState const *PathFinder::GetNeighbours(PathState const &State, size_t &Total) const
{
    // Temporary neighbour buffer...
    PathState Neighbours[8];

    // Bounds check...
    assert(State.GetX() < CHECKERBOARD_DIMENSION && 
           State.GetY() < CHECKERBOARD_DIMENSION);

    // We will count the total number of neighbours for caller we find...
    Total = 0;

    // Search for neighbours...

        // Anything to the north west?
        if(State.GetX() > 0 && State.GetY() < (CHECKERBOARD_DIMENSION - 1) && 
           !GetGridSquare(State.GetX() - 1, State.GetY() + 1))
            Neighbours[Total++] = PathState(State.GetX() - 1, State.GetY() + 1);

        // Anything to the north?
        if(State.GetY() < (CHECKERBOARD_DIMENSION - 1) && 
           !GetGridSquare(State.GetX(), State.GetY() + 1))
            Neighbours[Total++] = PathState(State.GetX(), State.GetY() + 1);

        // Anything to the north east?
        if(State.GetX() < (CHECKERBOARD_DIMENSION - 1) && State.GetY() < (CHECKERBOARD_DIMENSION - 1) && 
           !GetGridSquare(State.GetX() + 1, State.GetY() + 1))
            Neighbours[Total++] = PathState(State.GetX() + 1, State.GetY() + 1);

        // Anything to the east?
        if(State.GetX() < (CHECKERBOARD_DIMENSION - 1) && 
           !GetGridSquare(State.GetX() + 1, State.GetY()))
            Neighbours[Total++] = PathState(State.GetX() + 1, State.GetY());

        // Anything to the south east?
        if(State.GetX() < (CHECKERBOARD_DIMENSION - 1) && State.GetY() > 0 && 
           !GetGridSquare(State.GetX() + 1, State.GetY() - 1))
            Neighbours[Total++] = PathState(State.GetX() + 1, State.GetY() - 1);

        // Anything to the south?
        if(State.GetY() > 0 && !GetGridSquare(State.GetX(), State.GetY() - 1))
            Neighbours[Total++] = PathState(State.GetX(), State.GetY() - 1);
            
        // Anything to the south west?
        if(State.GetX() > 0 && State.GetY() > 0 && !GetGridSquare(State.GetX() - 1, State.GetY() - 1))
            Neighbours[Total++] = PathState(State.GetX() - 1, State.GetY() - 1);

        // Anything to the west?
        if(State.GetX() > 0 && !GetGridSquare(State.GetX() - 1, State.GetY()))
            Neighbours[Total++] = PathState(State.GetX() - 1, State.GetY());

    // Store for caller...
    PathState  *pNeighbours = new PathState[Total];
    for(unsigned int Index = 0; Index < Total; ++Index)
        pNeighbours[Index] = Neighbours[Index];
        
    // Return to caller...
    return pNeighbours;
}

```

Any help is much appreciated.

Kip

---

### Post by kwyto on 2009-12-30
the code is just to long to look at. I would look into Breadth Search First and Shortest Path Alg. The problem you are having is that whenever the algorithm checks for an empty space it starts with the diagonal ( as you can see from the pictures ), then instead of checking again the diagonal, it checks to the right of its position. look in the code where this is done and change the order, or optimize it, of the check for available squares.

---

### Post by kiplingw on 2009-12-30
> **kwyto said:**
> the code is just to long to look at. I would look into Breadth Search First and Shortest Path Alg. The problem you are having is that whenever the algorithm checks for an empty space it starts with the diagonal ( as you can see from the pictures ), then instead of checking again the diagonal, it checks to the right of its position. look in the code where this is done and change the order, or optimize it, of the check for available squares.

Hey kwyto. I am aware of breadth search and shortest path, but A* is necessary for my needs (it always finds optimized route if there is one, and in finite time).

I see what you mean how in GetNeighbours() it looks at the diagonal first, but should that make any difference when it checks all surrounding squares and not just the diagonal since the one with the shortest path will be used?

Also, what do you mean by instead of checking again the diagonal, it checks to the right of its position?

I guess I don't understand why the order it checks the neighbours matters since it investigates all of them?

Thanks for your help and yes the code is long, but the alternative was that someone would have asked for it.

---

### Post by kwyto on 2009-12-30
ok, i get what you are saying >  I see what you mean how in GetNeighbours() it looks at the diagonal first, but should that make any difference when it checks all surrounding squares and not just the diagonal since the one with the shortest path will be used? , in both pictures it chooses the right square, or square below, of its position. maybe that's it's just coincidence, but i don't think so. maybe someone might give you a better solution. is this all the code?

---

### Post by kiplingw on 2009-12-30
Hey Kwyto. I managed to get it working and thank you for your thoughtful reply.

I have managed to fix it (at least for all the scenarios I have tried, above inclusive).

Here is what I did:
Changed CostToGoalHeuristic to work as follows ```
return sqrt(pow(abs(From.GetX() - Goal.GetX()), 2) + pow(abs(From.GetY() - Goal.GetY()), 2));
``` 

This allows for Euclidean distance to be used which is admissible (an underestimate) and appropriate for when diagonal moves are permitted.

I also changed the CostToNeighbour as such...
```
// Determines cost of traversal from node to neighbour...
float PathFinder::CostToNeighbour(
    PathAgent const &Agent, PathState const &From, PathState const &Neighbour) const
{
    // Sanity check...
    assert((abs(From.GetX() - Neighbour.GetX()) == 1) || 
           (abs(From.GetY() - Neighbour.GetY()) == 1));

    // Lateral moves cost unity...
    if((From.GetX() == Neighbour.GetX()) || (From.GetY() == Neighbour.GetY()))
        return 1.0f;

    // Diagonal moves cost a big more... (root 2)
    else
        return 1.41421f;
}
``` 

It seems to work (for now). :)

Kip

---

