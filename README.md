# pyomoexamples
Working with Pyomo


Pyomo Solvers and Solver Managers
---------------------------------
Pyomo uses 'solver managers' to execute 'solvers' that perform
optimization and other forms of model analysis.  A solver directly
executes an optimizer, typically using an executable found on the
user's PATH environment.  Solver managers support a flexible mechanism
for asyncronously executing solvers either locally or remotely.  The
following solver managers are available in Pyomo:

    neos       Asynchronously execute solvers on the NEOS server
    phpyro     Specialized PH solver manager that uses pyro
    pyro       Execute solvers remotely using pyro
    serial     Synchronously execute solvers locally

If no solver manager is specified, Pyomo uses the serial solver
manager to execute solvers locally.  The pyro and phpyro solver
managers require the installation and configuration of the pyro
software.  The neos solver manager is used to execute solvers on the
NEOS optimization server.


Serial Solver Interfaces
------------------------
The serial, pyro and phpyro solver managers support the following
solver interfaces:

    asl                  + Interface for solvers using the AMPL Solver
                           Library
    baron                  The BARON MINLP solver
    bilevel_blp_global   + Global solver for continuous bilevel linear
                           problems
    bilevel_blp_local    + Local solver for continuous bilevel linear
                           problems
    bilevel_bqp          + Global solver for bilevel quadratic
                           problems
    bilevel_ld           + Solver for bilevel problems using linear
                           duality
    cbc                    The CBC LP/MIP solver
    conopt                 The CONOPT NLP solver
    contrib.gjh            Interface to the AMPL GJH "solver"
    cplex                  The CPLEX LP/MIP solver
    cplex_direct           Direct python interface to CPLEX
    cplex_persistent       Persistent python interface to CPLEX
    gams                   The GAMS modeling language
    gdpbb                * Branch and Bound based GDP Solver
    gdpopt               * The GDPopt decomposition-based Generalized
                           Disjunctive Programming (GDP) solver
    glpk                 * The GLPK LP/MIP solver
    gurobi                 The GUROBI LP/MIP solver
    gurobi_direct          Direct python interface to Gurobi
    gurobi_persistent      Persistent python interface to Gurobi
    ipopt                * The Ipopt NLP solver
    mindtpy              * MindtPy: Mixed-Integer Nonlinear
                           Decomposition Toolbox in Pyomo
    mosek                  Direct python interface to Mosek
    mpec_minlp           + MPEC solver transforms to a MINLP
    mpec_nlp             + MPEC solver that optimizes a nonlinear
                           transformation
    multistart           * MultiStart solver for NLPs
    path                   Nonlinear MCP solver
    pico                   The PICO LP/MIP solver
    ps                   * Pyomo's simple pattern search optimizer
    py                   + Direct python solver interfaces
    scip                   The SCIP LP/MIP solver
    trustregion          * Trust region filter method for black
                           box/glass box optimization
    xpress               * The XPRESS LP/MIP solver

An asterisk indicates solvers that are currently available to be run
from Pyomo with the serial solver manager. A plus indicates meta-
solvers, that are always available.

Pyomo also supports solver interfaces that are wrappers around third-
party solver interfaces. These interfaces require a subsolver
specification that indicates the solver being executed.  For example,
the following indicates that the ipopt solver will be used:

   asl:ipopt

The asl interface provides a generic wrapper for all solvers that use
the AMPL Solver Library.

Note that subsolvers can not be enumerated automatically for these
interfaces.  However, if a solver is specified that is not found,
Pyomo assumes that the asl solver interface is being used.  Thus the
following solver name will launch ipopt if the 'ipopt' executable is
on the user's path:

   ipopt


NEOS Solver Interfaces
----------------------
The neos solver manager supports solver interfaces that can be
executed remotely on the NEOS optimization server.  The following
solver interfaces are available with your current system
configuration:

    bonmin       Heuristic MINLP solver
    cbc          MILP solver
    conopt       Feasible path NLP solver
    couenne      Exact MINLP solver
    cplex        MILP solver
    filmint      Heuristic MINLP solver
    filter       SQP NLP solver
    ipopt        Interior point NLP solver
    knitro       Convex MINLP solver
    l-bfgs-b     Bound-constrained NLP solver
    loqo         Interior point NLP solver
    minlp        Heuristic MINLP solver
    minos        SLC NLP solver
    minto        MILP solver
    mosek        Interior point NLP solver
    ooqp         Convex QP solver
    path         Nonlinear MCP solver
    snopt        SQP NLP solver
