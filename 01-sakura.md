![Sakura](http://readevalprintlove.fogus.me/images/sakura_etegami.jpg)

Sakura
======

*Read-Eval-Print-λove is a bi-monthly newsletter of original content and curation about the Lisp family of programming languages and little-languages.*

---

One day the macrolyte approached the master macrologist
Pi Mu (Πム) and put forth a question:

> Master, which Lisp is the greatest of all Lisps?

Pi Mu looked at the macrolyte and, in a low tone, told him 
to meet him in the garden after the day's work was done and he would tell him the answer.

After a long day's toil[^toil] the macrolyte did as Pi Mu instructed 
and met him at the entryway to the humble garden.  He 
immediately posed his question again:

> Master, which Lisp is the greatest of all Lisps?

In a careful manner Pi Mu then pointed at a patch of nearby sakura and said:

> Look here at this patch of sakura.
>
> What a tall one that one.
>
> What a short one that one.

The student was at once enlightened.

[^toil]: Not nearly as rigorous as Pi Mu's however.

---

The theme of this installment of Read-Eval-Print-λove is: musings on the function, nature, differences and commonalities of the Lisp family of languages in general.


Dedication
==========

![September 4, 1927 – October 24, 2011](http://readevalprintlove.fogus.me/images/jmc.jpg)


# What's Lisp?

In 1980 John McCarthy wrote a paper entitled *[LISP - Notes on its past and future][lisp-fu]* for Stanford's Lisp conference that year.  With in the paper he listed fifteen points that he claimed characterized LISP, shown in-full below:

  1. Computing with symbolic expressions rather than numbers.
    
  2. Representation of symbolic expressions and other information by
     list structure in computer memory.
	  
  3. Representation of information on paper, from keyboards and in
     other external media mostly by multi-level lists and sometimes by
     S-expressions. It has been important that any kind of data can be 
     represented by a single general type.
	  
  4. A small set of selector and constructor operations expressed as
     functions, i.e. `car`, `cdr` and `cons`.
	  
  5. Composition of functions as a tool for forming more complex
     functions.
			 
  6. The use of conditional expressions for getting branching into
     function definitions.
	 
  7. The recursive use of conditional expressions as a sufficient tool
     for building computable functions.
	 
  8. The use of λ-expressions for naming functions.
	   
  9. The storage of information on the property lists of atoms.
		   
  10. The representation of LISP programs as LISP data that can be
      manipulated by object programs. This has prevented the
      separation between system programmers and application
	  programmers. Everyone can *improve* his LISP, and many of 
	  these *improvements* have developed into improvements to 
	  the language.
		
  11. The conditional expression interpretation of Boolean
      connectives.
 
  12. The LISP function `eval` that serves both as a formal 
      definition of the language and as an interpreter.
	  
  13. Garbage collection as the means of erasure.
	    
  14. Minimal requirements for declarations so that LISP 
      statements can be executed in an on-line environment [^repl]
	  without preliminaries.
	  
  15. LISP statements as a command language in an on-line 
      environment.
	 
Under these conditions, what current languages are Lisps?  Which fall short? [^more-lisp]

[^repl]: Think REPL.

[lisp-fu]: http://www-formal.stanford.edu/jmc/lisp20th.html)

[^more-lisp]: I'll come back to this list in future installments. Stay tuned.

## Related reading

The following links explore the question:

> What is a Lisp, and am I it?

 * [The Nature of Lisp](http://www.defmacro.org/ramblings/lisp.html) by Slava Akhmechet
 * [What Made Lisp Different][diff] by Paul Graham
 * [Why Ruby is an Acceptable Lisp][lirb] by Eric Kidd
 * [Lisp is Not an Acceptable Lisp][lispnot] by Steve Yegge
 * [Why I Ignore Clojure][why-ig] by Manuel Simoni
 * [Why Scala is an Acceptable Lisp][lisca] by Will Fitzgerald
 * [Plotting and Scheming the Ubiquitous LISP][plotting] by André van Meulebrouck
 * [What can Lisp do that Lua can't?](http://stackoverflow.com/questions/323346/what-can-lisp-do-that-lua-cant)
	 
If you walk through this list focusing your lens of reason onto various programming languages then which ones make the cut?

![Possibly maybe](http://readevalprintlove.fogus.me/images/maybe.png "Sorta display your Lisp pride!")

One interesting consequence that falls out of adhering strictly to the list above is that those that meet many of the criteria tend to be little languages (another aspect I will explore from time to time).  For example, Lua[^lua] meets many of the criteria above, but is it a Lisp?  Likewise, even Common Lisp falls short on at least one[^std] of McCarthy's criteria and many of the remaining points, while supported, are not considered central to "the Common Lisp way." [^clway]

[^lua]: Lua is very close to meeting all of the requirements above and with [MetaLua](http://metalua.luaforge.net/) is darn near complete.

[^std]: A relience on the Common Lisp standard for language definition leads me to believe that `eval` is an insufficient mechanism for describing the nuances of CL.

[^clway]: To the extent that Common Lisp has or supports a "way."


## Who's Lisp?

Just because MacCarthy invented Lisp doesn't mean that he has the right to define what constitutes a Lisp.  This seems like a counter-intuitive thing to say, but the fact is that Lisp has grown far beyond anything that McCarthy imagined at the time that he defined the first `eval`.  Vendors, users, programmers, standards committees and implementers have a say also.

![Erik Naggum](http://readevalprintlove.fogus.me/images/naggum.jpg)

Pinning down what constitutes a Lisp based on McCarthy's list above is a tough task that is due to exclude many participants with partial (and often legitimate) claims to the feature set above. [^scmnot]  On the other hand, simply taking an implementation like Common Lisp as the model of "Lispiness" is unsatisfactory as well since doing so excludes historical Lisps that fed into the development of the Common Lisp standard.  So maybe the right answer to "what is Lisp?" is simply -- "who cares?"[^idont]  For the purposes of this zine[^zine] I'll freely mix discussion and examples for various Lisp implementations both current and historical and not worry too much about identity issues.

[^idont]: I don't really care, but I'll still try to use the terms "Lisp family" vs. "Little language" vs. some other terms to make a distinction.

[^scmnot]: There was an epic thread on the comp.lang.lisp Usenet list circa 2002 involving part trolling, part rage and part wisdom entitled *[Why Scheme is not a Lisp?](https://groups.google.com/forum/#!topic/comp.lang.lisp/Bj8Hx6mZEYI)*.  It's well worth exploring that thread for a deeper understanding of just what constitutes a Lisp and how Internet communications will be the death of us all.

[^zine]: The tern "zine" is a bit archaic, but I've not thought of a better term for what this is.  I was considering "xine", but that's not really satisfactory either.

[diff]: http://www.paulgraham.com/diff.html

[lirb]: http://www.randomhacks.net/articles/2005/12/03/why-ruby-is-an-acceptable-lisp

[lispnot]: http://steve-yegge.blogspot.com/2006/04/lisp-is-not-acceptable-lisp.html

[lisca]: http://willwhim.wpengine.com/2013/02/22/why-scala-is-an-acceptable-lisp

[why-ig]: http://axisofeval.blogspot.com/2010/04/why-i-ignore-clojure.html

[plotting]: http://web.archive.org/web/20051211071852/http://fresh.homeunix.net/files/ilc02/proceedings/Andre-van-Meulebrouck.pdf


# The German School of Lisp [^revisited]

Allow me to take a few moments to broadly segment the Lisp ecosystem into high-level categories, namely: Extension Lisps, Practical Lisps, Kernel Lisps and Lisps targeting education.

Of course, there are overlaps between these categories for any given Lisp instance, and you may not agree with certain placements or even the categories themselves.  That said, please humor me as I'm trying to establish a basis for an observation that there exist a category of Lisp-like languages that do not fall into any of these categories and in some ways cover them all -- blurring the line between the above categories while touching each, yet existing in a category that only exists by occlusion -- much like [Kanizsa's Triangle][kan].

![Lisps](http://readevalprintlove.fogus.me/images/lisps.png "The space between")

[^revisited]: This is an expanded and updated version of an [earlier article "The German School of Lisp" from 2011](http://blog.fogus.me/2011/05/03/the-german-school-of-lisp-2/).

[kan]: http://www.michaelbach.de/ot/cog_kanizsa/index.html

## Exo-Lisps

Exo-Lisps are the variants that exist to serve very pointed use cases.  They can take the form of highly specialized libraries or embeddables like the Scheme-based object system [GLOS](http://people.csail.mit.edu/gregs/ref-dyn-patterns.html) or the graphics-rich programming language [Lush](http://lush.sourceforge.net/).

{lang="scm"}
    ;; Using GLOS types and multiple dispatch to 
	;; implement the Builder pattern (Sullivan 2002)
    (add-method* convert
	  (method ((builder <tex-converter>) (token <char>))
		. . . convert TeX character . . . )
	  (method ((builder <tex-converter>) (token <font>))
		. . . convert TeX font change . . . )
	  (method ((builder <text-widget-converter>) (token <char>))
		. . . convert text widget character . . . )
	  (method ((builder <text-widget-converter>) (token <font>))
		. . . convert text widget font change . . . ))

Likewise, Exo-Lisps may be embedded within existing applications, like [Emacs Lisp](http://www.gnu.org/software/emacs/emacs-lisp-intro/), or act as extension frameworks like [Guile](http://www.gnu.org/s/guile/), [Visual Lisp](http://usa.autodesk.com/adsk/servlet/index?siteID=13112&id=770237) and [Elk](http://sam.zoy.org/elk/).

{lang="cl"}
    ;; Using Emacs Lisp to insert text around a region (Lee 2005)
    (defun wrap-markup-region (start end)
	  "Insert a markup <b></b> around a region."
      (interactive "r")
	  (save-excursion
        (goto-char end) (insert "</b>")
        (goto-char start) (insert "<b>")))

Finally, Exo-Lisps like [LFE](https://github.com/rvirding/lfe) and [Liskell](http://lambda-the-ultimate.org/node/2363) serve as skins over the semantics of another language.

{lang="cl"}
    ;; Creating an Erlang process and sending it a message with LFE
    (set say (lambda () 
	           (receive 
                 (msg (: io format '"'~s'~n" 
                                   (list msg))))))
	 
    (set sayer (spawn (lambda () (funcall say))))
	
	(! sayer "Hello Cleveland!")

While Exo-Lisps are often practical, they are not always used to build total systems.  Instead, the practical Lisps in the next section would most likely be used.

## Practical Lisps

Practicality is a relative term.  Having said that, there are clearly a set of Lisps that exist primarily to solve "real world" [^real] problems and to typically build stand alone applications, including: [Common Lisp](http://common-lisp.net/), [Clojure](http://clojure.org), [Scheme (R5RS, R6RS, R7RS-big)](http://www.schemers.org/), [Racket](http://racket-lang.org/), [Chicken Scheme](http://www.call-cc.org/), and [Dylan](http://www.opendylan.org/).  

{lang="cl"}
    ;; Using Clojure for street lane detection from 
	;; video source -- elided (Nakkaya 2011)
    (defn detect-edges [i]
      (--> (convert-color i :bgr-gray)
	       (smooth :gaussian 7 7 0 0)
           (canny 90 90 3)))
    
    (defn process-frame [f w h]
	  (let [roi (copy-region f 0 50 w (- h 50))
            edges (detect-edges roi)
	        points (points edges)
	   	    lane  (map #(let [[x y] %] [x (+ y 50)]) 
			           (filter (polygon points)))]
        (poly-line f lane java.awt.Color/blue 4)
	    (release [roi edges])))
	
	(let [capture (capture-from-file "StayingInLane_MPEG4.avi")
	      frame-count (get-capture-property capture :frame-count)
	      width (get-capture-property capture :frame-width)
	      height (get-capture-property capture :frame-height)]
      (dotimes [_ frame-count]
	    (let [frame (query-frame capture)]
	      (process-frame frame width height)
          (view :raw frame)
	      (Thread/sleep 10)))
      (release capture))

I'm tempting charges of libel by including this particular category and filling it with these particular choices, but so be it.

[^real]: I really hesitate to use the term "real world" because it's often used to categorize highly fashionable or mainstream jobs or markets.  However, *my* "real-world" involves distributed simulations and production rules systems, two somewhat specialized fields.  Sadly, I think that "real world" is a place where programmers retreat to avoid learning something new and possibly challenging.

## Kernel Lisps

I struggled to find a way of separating Exo-Lisps and Kernel Lisps and the following distinction arose from this struggle.  Where Exo-Lisps serve as a framework for a specific problem, Kernel Lisps serve as a framework for a more general problem  -- language or system development and experimentation.  Some examples of Kernel Lisps include: [R7RS-small](https://groups.google.com/forum/#!topic/comp.lang.scheme/MCfPoeir90s), [Scheme48](http://s48.org), [Lisp Machine Lisp](http://common-lisp.net/project/bknr/static/lmman/frontpage.html), [EuLisp](http://people.bath.ac.uk/masjap/EuLisp/eulisp.html), and [Kawa](http://www.gnu.org/software/kawa/).

{lang="cl"}
    ;; A ZetaLisp locking example
    (unwind-protect
      (progn (process-lock sentinel)
        (do-something)
        (do-something-else))
      (process-unlock sentinel))

Perhaps I'm splitting hairs.

{lang="scm"}
    ;; Defining a record type in Scheme-48
    (define-record-type tuple :tuple
	  (make-tuple ent attr val)
      tuple?
	  (ent get-entity)
	  (attr get-attribute)
	  (val get-value))

The topic of Kernel Lisps could fill a volume of books (and has!), but a deeper exploration will need to wait until another day.

## Pedagogical Lisps

As I alluded to earlier, the [Lisp landscape is rife with toys](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=toy+lisp), [Ur-Lisps](http://axisofeval.blogspot.com/2010/08/no-more-minimal-early-lisps-pulleezz.html), undergraduate interpreter projects and half implementations.

{lang="ruby"}
    # The base environment for an Ur-Lisp written in Ruby
    @env = { 
	 :label => proc { |(name,val), _| @env[name] = eval(val, @env) },
     :car   => lambda { |(list), _| list[0] },
	 :cdr   => lambda { |(list), _| list.drop 1 },
     :cons  => lambda { |(e,cell), _| [e] + cell },
	 :eq    => lambda { |(l,r),ctx| eval(l, ctx) == eval(r, ctx) },
     :if    => proc { |(c,t,e),ctx| eval(c, ctx) ? eval(t, ctx) : eval(e, ctx) },
     :atom  => lambda { |(s), _| (s.is_a? Symbol) or (s.is_a? Numeric) },
     :quote => proc { |sexpr, _| sexpr[0] } }

However, the vast majority of these Lisps exist for pedagogical pursuits and are rarely (if ever) overtly practical[^overt].  That's not to say that there is no value in pedagogical Lisps.  I'm a strong advocate of using small Lisp implementations as a programmer's fruit fly (i.e. a model "organism" for understanding languages and computation).

## Fluchtpunkt Lisps

The German school of Lisp is described by [Kazimir Majorinc][kaz] as a Spartan movement[^mini] in Lisp implementation.[^toys]  While I can agree with this categorization, I think that there's more to the German school than just one aspect.  In fact, I would say that to meet the criteria of the German school, a Lisp must take a philosophical stand in its implementation.

I'd like to propose a new term for the kinds of Lisps that fall into this "school" classified largely by their Spartan natures.  

Recall the graphic from the beginning of this article:

![Lisps](http://readevalprintlove.fogus.me/images/lisps.png "The space between")

This section deals with the crimson space between, affectionetly refered to as *Fluchtpunkt Lisp*.

Fluchtpunkt Lisps skirt the vanishing point (in German, *der fluchtpunkt*) between theory, practicality and art.  These implementations are all of the other categories in some way, while simultaneously being none in particular.  These Lisps are not libraries nor do they typically have full-blown development ecosystems like the four higher-level categories outlined above.  They may or may not be general purpose languages in all instances, but they are **all driven by a fervent ideal**.  

Below is a list of Fluchtpunkt Lisp implementations that I've found, and some discussion of their driving ideal (as I understand):

[kaz]: http://kazimirmajorinc.blogspot.com/2011/04/one-picolisp-snippet.html

[^toys]: But let me be clear, the Lisps in this section are not toys like the ones littering the Lisp landscape (including, and especially, my own: [Lithp][lithp] and [μLithp][ulithp]).

[lithp]: http://github.com/fogus/lithp

[ulithp]: http://github.com/fogus/ulithp

### T

<http://mumble.net/~jar/tproject/>

T is my favorite Scheme variant and the inspiration for many a Lisp/Scheme/Clojure thereafter.  I've poured over Stephen Slade's T book [^t-book] numerous times, finding something mind blowing each time.  The primary driving force behind T was to prove that a Scheme could be made to run extremely fast, and fast it ran.  T's compiler technology was the motivation for numerous dissertations, and remains influential in many ways, even if some of its compilation techniques have fallen out of fashion.  T had a notion of a first-class environment (called locales) that formed the basis of its dynamic module system.  However, one very important lesson in T was that its core was built from a set of base-objects and the implementation is a master-class in abstraction and API design.

{lang="scm"}
    ;; An example of delay/force functions in T
	;; from (Rees 1988)
	
	(DEFINE-SYNTAX (DELAY EXP)                      <1>
	  `(MAKE-DELAYED-OBJECT (LAMBDA () ,EXP)))

	(DEFINE (MAKE-DELAYED-OBJECT THUNK)
	  (LET ((FORCED-YET? NIL)
	        (FORCED-VALUE NIL))
	    (OBJECT NIL                                 <2>
	            ((FORCE SELF)
	             (COND ((NOT FORCED-YET?)
	                    (SET FORCED-VALUE (THUNK))  <3>
	                    (SET FORCED-YET? T)))
	             FORCED-VALUE))))

	(DEFINE-OPERATION (FORCE OBJ) OBJ)

  1. A macro to avoid evaluation
  2. `OBJECT` creates an anonymous class responding to a `FORCE` message
  3. Calling the `THUNK`

The names attached to T development is an all-star roster of langdev[^langdev] including, but not limited to: [Kent Pitman](http://www.nhplace.com/kent/), [Jonathan Rees](http://mumble.net/~jar/), [Richard Kelsey](http://mumble.net/~kelsey/), [Paul Hudak](http://www.cs.yale.edu/people/hudak.html) and [Olin Shivers](http://www.ccs.neu.edu/home/shivers/).  T is an inspiration.

[^langdev]: Programming language development.

[^t-book]: http://www.amazon.com/o/asin/013881905X?tag=fogus-20

### Shen

<http://shenlanguage.org/>

Shen (and its predecessor Qi) really pushes the limits of what we might call a Fluchtpunkt Lisp.  I suspect it requires a categorization of its own.  

A few years ago I was looking for a Lisp to dive into and my searching uncovered two extremely interesting options: Clojure and Qi.  I eventually went with Clojure, but in the intervening time I've managed to spend quality time with Qi and I love what I've seen so far.  Qi's confluence of features, including an optional type system (actually, its type system might be more accurately classified as "skinnable"), pattern matching,[^patt] and an embedded logic engine based on Prolog, make it a very compelling choice indeed.

{lang="scm"}
    \\ Defining card rank and suit types using Shen
	\\ from http://www.shenlanguage.org
	
	(datatype rank
	  if (element? X [ace 2 3 4 5 6 7 8 9 10 jack queen king])
	  ________
	  X : rank;)

	(datatype suit
	  if (element? Suit [spades hearts diamonds clubs])
	  _________
	  Suit : suit;)

	(datatype card
	  Rank : rank; Suit : suit;
	  ==================
	  [Rank Suit] : card;)

Aside from the type system and the embedded Prolog Shen also supports function definition as successive pattern matching forms.

{lang="scm"}
	(define get-suit
	  {card --> suit}
	  [Rank Suit] -> Suit)  <1>

	(get-suit [2 hearts])

    \\> hearts : suit

  1. Pattern match on the 2-tuple and return the right element

There is also a book entitled *The Book of Shen* by the language's creator Mark Tarver available at <http://www.fast-print.net/bookshop/1278/the-book-of-shen>.

### newLISP

<http://www.newlisp.org/>

newLISP raised some ire at one point or another because of its design choices, specifically its choice of pervasive dynamic scope and [fexprs](http://www.wpi.edu/Pubs/ETD/Available/etd-090110-124904/unrestricted/jshutt.pdf) (pdf).[^fexprs]  I like dynamic scope under some circumstances, but I can't say that I've followed it to its logical end for any application of significant size or complexity.  The advocates of newLISP are interesting folk and in many ways of my own mind.  For example, how would one [calculate Pi out to `n` digits in newLISP]()?

{lang="newlisp"}
    (define (pi n)
      (replace "\\" 
        (join                                        <1>
          (exec                                      <2>
            (format 
              "echo 'scale=%d; 4 * a(1)' | bc -ql"   <3>
              n)))
        ""))
    
    (pi 30) 
    ;;=> "3.1415926535897932384626433832795028841968"

  1. Wait for the result from a child process
  2. Spawn a child process
  3. Build the UNIX command as a string

Why you would call out to the UNIX `bc` command of course.

Why would you need your programming language to provide that type of calculation[^mul] when there are more appropriate tools for doing so?  This is a question asked, and answered by newLISP. 

I suppose the fundamental philosophy of newLISP is to not necessarily provide everything, but to make everything possible.  newLISP facilitates possibility by treating the use of `eval` as a first-class approach and utterly idiomatic.

### Arc

<http://www.paulgraham.com/arc.html>

I agonized over including Paul Graham's Arc in the category of Fluchtpunkt Lisp, but I think this is the correct place for it.  The driving forces behind Arc are [succinctness][1] and [centenarianism][2] -- both of which are certainly emblematic of the Fluchtpunkt ideal.  Arc hasn't taken off [as much as non-Paul-Graham humans would have liked][pg], but I believe that the root of the problem is that they prayed for practical, but instead got Fluchtpunkt.

{lang="scm"}
	;; The HackerNews source code for determining an article's rank on the
	;; front page, elided

	(= gravity* 1.8 timebase* 120 front-threshold* 1 
	   nourl-factor* .4 lightweight-factor* .3 )
	   
	(def frontpage-rank (s (o scorefn realscore) (o gravity gravity*))
	  (* (/ (let base (- (scorefn s) 1)
	          (if (> base 0) (expt base .8) base))
	        (expt (/ (+ (item-age s) timebase*) 60) gravity))
	     (if (no (in s!type 'story 'poll))  1
	         (blank s!url)                  nourl-factor*
	         (lightweight s)                (min lightweight-factor* 
	                                             (contro-factor s))
	                                        (contro-factor s))))

In general, the development pace of Arc is slow and generally tied directly to changes required to keep Hacker News running, but a [community of Arc fanatics][3] has taken the torch and created various implementations and references for Arc.

[1]: http://www.paulgraham.com/power.html
[2]: http://www.paulgraham.com/hundred.html
[pg]: http://www.arclanguage.org/item?id=8462
[3]: https://sites.google.com/site/arclanguagewiki/home 

### PicoLisp

<http://www.picolisp.com/>

I first came across PicoLisp when reading the paper ["Pico Lisp: A Radical Approach to Application Development"](http://software-lab.de/radical.pdf) by  Alexander Burger and was instantly fascinated.  The primary goal is to provide an idealized Lisp interpreter that runs as fast as possible.  To accomplish this goal PicoLisp limits its feature set and optimizes the code path along the dimensions of its features.  The core types provided by PicoLisp are numbers, symbols, and lists.  Given the paucity of these types PicoLisp has the advantage of always taking the most direct interpretation path and thus avoiding any unnecessary checks and abstractions that a more corpulent Lisp might require.  For example, PicoLisp's `quote` function is defined in such a way that it [returns all of its arguments unevaluated](http://picolisp.com/5000/!wiki?ArticleQuote) allowing the operation of `quote` to optimize into only a return of its `cdr` rather than the `car` of its `cdr`.  Simple no?

Another interesting aspect of PicoLisp is that is does not contain strings, arrays, vectors nor anything but exactly numbers, symbols and lists as first-class data types.  It's drive is for simplicity [^simpl] in its offerings and possibilities as well as its implementation.  Aside from the practical matter that offering more data types means that there would be more type-specific functions, on the implementation side an increase in the  [number of tag-bits](http://picolisp.com/5000/!wiki?ArrayAbstinence) is a limiting factor as well.  If you need a string, use a symbol.  If you need an array, use a list.  And so on...

Here is an example of some PicoLisp to scape a web-page:

{lang="cl"}
    (load "@lib/http.l")
    	 
    (client "replove.herokuapp.com" 80 "sakura/index.html" <1>
      (when (from "Pi Mu ")                                <2>
        (pack (trim (till "and")))))                       <3>
    
    ;;=> (Πム)

  1. Attach to the page using the built-in client library
  2. Start reading bytes from a given string
  3. Stop reading when it finds a different string

PicoLisp is, in my opinion, the most interesting entry in a family of *really really small Lisps* that also includes [Nanolisp](http://www-fourier.ujf-grenoble.fr/~sergerar/Nanolisp/) and [femtoLisp](http://code.google.com/p/femtolisp/), although I would hesitate to include these latter two in the Fluchtpunkt category. Even with its minimal data types, minimal scoping rules (dynamically scoped) and its favoring of `eval` over macros, PicoLisp still offers some interesting features like co-routines, first-class environments, and integrated database and Prolog (Pilog).

[^simpl]: The word "simple" is used in a loose way throughout this issue and is not tied to its dual "entangled" nor "complected."

### Wasp Lisp

<http://sites.google.com/site/waspvm/>

Wasp Lisp is a small Scheme inspired by Erlang with lightweight cooperative threads, communication via channels, and an implementation of [MOSREF](http://bc.tech.coop/blog/061119.html).  This latter feature is fairly interesting in that it allows one to create a network of "drone" Wasp VMs that can receive secure snippets of code from a remote console for execution.  

## What is Fluchtpunkt?

Fluchtpunkt Lisps are...

1. **Focused**: Uncompromising in their vision
2. **Spartan**: Devoid of the seemingly unnecessary comforts found in many modern languages
3. **Controversial**: Not always by design, but often because of their design
4. **Fun**

I've taken a swing at a Fluchtpunkt Lisp or two, but haven't really put my heart into it -- and that's a problem because Fluchtpunkt Lisps require heart.

[^overt]: However, toy and Ur-Lisps are practical insomuch as the act of implementing them is good programming practice.

[^fexprs]: Regardless of the chances of bringing a libel suit on myself, I will say that fexprs are effectively runtime macros. 

[^mul]: Well, you could also use `(mul 4 (atan 1))` if you didn't care about precision. :p

[^mini]: I intentionally avoid the word "minimal" in this post.  Spartan is Mr. Majorinc's word, and I think it is more appropriate.

[^patt]: I miss pattern matching.  `clojure.core.match`, wherefore art thou?


# A language that doesn't let you affect the way it thinks is not worth growing

The differences between Common Lisp and Scheme are numerous and deep, but one difference that truly stands out to newcomers is summarized as their respective Lisp-2 and Lisp-1 natures.  In a sentence, Lisp-1 refers to a language that binds function values in the same namespace as any other values while a Lisp-2 binds function values in a separate namespace from other kinds of values.  The mechanics of [^lisp-n] namespacing are not important for this section, but I'll probably talk about it more in future installments.

[^lisp-n]: Common Lisp has many more than two namespaces for binding certain values to names.  I could (and probably will) write a whole issue on just this topic.

One way that this difference manifests itself is in endless, mostly pedantic Usenet threads and blog posts.  However, the other manifestation is in the way that higher-order and first-class functions are built.  Take for example a `best` function implemented in Common Lisp that takes a function and a list and returns the "best" value based on the pairwise criteria encoded in the given function:

{lang="cl"}
    ;; Common Lisp -- bad example

    (defun best (fun list)
      (reduce (lambda (x y) 
                (if (fun x y) x y))
              list))

When the `best` function is called with a function value it is bound to the name `fun`.  However, Common Lisp has careful logic around how it looks up an operator (the thing at the head of a list).  That is, Common Lisp will look at the *name* `fun` rather than its value and attempt to look it up in the function namespace rather than resolving its value.  You're not likely to have a `best` function available, so attempting to call it as written above will failed with a function-lookup-error.  Instead, if the above were Scheme code (with a slightly different function definition syntax) then everything would work as expected.

The correct way to write `best` is as follows:

{lang="cl"}
    ;; Common Lisp

    (defun best (fun list)
      (reduce (lambda (x y) 
                (if (funcall fun x y) x y))
              list))

Instead of placing `fun` at the head of a list the new implementation calls its value (hopefully a function) via the `funcall` function.  Common Lisp's `funcall` will indeed resolve the value of `fun` via normal argument evaluation and "do the right thing," as shown below:

{lang="cl"}
    (best #'> '(1 2 3 4 5 6 -1))
    ;;=> 6

Now something that might jump out at you if you're not familiar with Common Lisp is that the greater-than function `>` is passed using the `#'` prefix.  This prefix tells Common Lisp that a value passed is indeed a function and as a result its value should be obtained from the function namespace.

This drives Scheme programmers crazy.  That is, the extra ceremony around passing and calling functions is viewed as inelegant by many in the Scheme community.  Whether you agree with this view or not is not the point however.  Instead, I'd like to show that Common Lisp is flexible enough to facilitate a more Scheme-like ideal.

## Evolutionary by design

Common Lisp is a language that can host its own evolution.  That is, if you wish to make Common Lisp into a language of your dreams then you need only mold it into that language.  Have you ever wondered why the Common Lisp standard has not changed in so many years?  The straight answer is that it doesn't need to.  Instead, the standard defines Common Lisp in such a way as to allow language-level evolution in addition to not standing in the way of vendor-specific enhancements.  This stands in stark contrast to many programming language standards that define a specific language's capabilities in fixed terms.

One feature of Common Lisp that provides an edge in evolution over many (most?) languages is its `macrolet` special operator.  In short, `macrolet` defines a lexical block (like `let`) whereby expansions of embedded macros occur based on the local macro binds.  Observe a very simple use of `macrolet`:

{lang="cl"}
    (macrolet ((sq (n) `(* ~n ~n)))
      (sq 10))
    ;;=> 100

The expansion of the code above would be:

    (* 10 10)

Pretty straight-forward no?  

Now, using `macrolet` I can create a macro named `schemish`[^scm-macro] that takes a list of names and locally rewrites their invocations to occur through `funcall`.  That is, the following:

    (schemish (fun)
      (fun 10))

Would be expanded locally into:

    (funcall fun 10)

The implementation of `schemish` is as follows:

{lang="cl"}
    (defmacro schemish (functions &body body)
      `(macrolet ,(mapcar (lambda (function)
                    `(,function (&rest args)
                       `(funcall ,',function ,@args)))
                    functions)
          ,@body))

The use of `mapcar` in the implementation above builds a `macrolet` compatible bindings expression that binds any names as local macros that themselves expand into calls of the functions through `funcall`.  It's best to show an expansion:

{lang="cl"}
    (macroexpand '(schemish (fun) (fun 42)))

    ;;=> (MACROLET ((FUN (&REST ARGS) 
    ;;                (FUNCALL FUN ARGS)))
    ;;     (FUN 42))

Thus fully expanded, (you might see something different if you run it in your chosen REPL) the code above looks similar to the previous use of `macrolet` and `sq`.  Now, I can use `schemish` to avoid explicit use of `funcall` and (hopefully) placate some of the Scheme adherents:

{lang="cl"}
    (defun best (fun list)
      (schemish (fun)
        (reduce (lambda (x y) (if (fun x y) x y))
                list)))

And the use of the new `best` implementation is as follows:

{lang="cl"}
    (best #'> '(1 2 3 4 5 -1))
    ;;=> 5

    (best '< '(1 2 3 4 5 -1))
    ;;=> -1

One point of note in the examples above is that the symbol `<` was resolved to the correct function automatically.  This is a feature of `funcall` itself.  One character saved!

[^scm-macro]: The `schemish` macro is taken wholly from Erik Naggum (at https://groups.google.com/forum/#!topic/comp.lang.lisp/Bj8Hx6mZEYI%5B101-125) with the name changed for giggles.  I also removed his use of `locally` as I didn't want to get into a discussion of why it was or wasn't needed.  It's worth reading the original message for additional illumination.  You can enhance your reading by exploring his original code and my changes at <http://ideone.com/axfTIQ>.

## Conclusion

Both the Common Lisp and Scheme standards make fundamental decisions that define core precepts that define their behaviors and in many ways attract certain kinds of programmers.[^nope]  Additionally, both Scheme and Common Lisp allow degrees of language evolution through various means.  However, in my opinion there are no languages[^hmmm] in operation today that provide the flexibility and self-hosted evolution provided by Common Lisp.

[^nope]: I'll not discuss the "kinds" at all.  Sorry.

[^hmmm]: Debatable.


# Eating parentheses for breakfast is delicious... and fun!

*A review of [Land of Lisp][lol] by Dr. Conrad Barski.*

![Land of Lisp](http://readevalprintlove.fogus.me/images/lol.png)

[lol]: http://www.amazon.com/dp/1593272812/?tag=fogus-20

If for no other reason, you should [buy Land of Lisp][lol] because of the extreme levels of unadulterated nerdery filling its pages. The price of the book is almost worth that very spectacle alone. However, as an added bonus the content of the book is top drawer. The first incarnation of Lisp was discovered by John McCarthy over 50 years ago, so it's difficult to imagine that a book on the subject bringing a fresh perspective, but Land of Lisp pulls it off in spades. The book manages to carve its own unique niche in the Lisp book landscape through a masterful blend of cartoons, game development examples, interesting prose, and a highly sharpened whit.

![One of the many laugh-out-loud moments](http://readevalprintlove.fogus.me/images/dialect.png)

The author, [Conrad Barski M.D.][cb], takes the reader through a whirlwind tour of Common Lisp and some of the fundamental principles of game development, but interestingly enough it never feels rushed. He accomplishes this feat by sticking to a very important strategy summarized as, "providing something useful at every stage". That is, every example in the book is meant to fit into the context of the larger game examples (e.g. a text adventure, Dice of Doom, etc.) while simultaneously teaching a lesson about Common Lisp *and* provide utility in isolation. It's really a thing of beauty the way that Mr. Barski manages to build useable games piecemeal while teaching important concepts along the way. To illustrate what I mean, let me give an example.

The Dice of Doom game[^games] example starts with a very small 2x2 board and the program parts needed to represent it. Mr. Barski then builds pieces on top of this substrate to generate positions, while extolling the virtues of decoupling the logic of the game from its representation. It's at this point that the game is playable against a human opponent, but at no previous stage was the code left in a state of flux -- each one was fully amenable to tinkering, tweaking, and experimentation. As an added bonus, the whole implementation by this stage was an incredible 13 lines! (that is actually not true, it's more than that, but by using Common Lisp the implementation was incredibly concise) As if this feat was not impressive enough, Mr. Barski then adds game AI into the mix while explaining the famous minimax search algorithm. He then makes the game more efficient using some techniques common in functional programming, including: closures, memoization, tail-calls (with caveats), and lazy programming. As expected the game itself becomes more feature rich as these lessons progress as stronger AI (i.e. better evaluation) is added, more efficient search techniques are introduced (i.e. alpha-beta pruning), and heuristics are used.

All in all, I am very impressed with the quality of Land of Lisp and consider it one of the best Common Lisp book available today. As a [co-author of a Clojure programming book][joy] I appreciate the amount of effort required to pull off a genuinely unique book -- I would be happy to achieve a fraction of the quality of Land of Lisp. This book will appeal to the long-time Lisper and the neophyte and I highly recommend buying it today.

[^games]: As a fan of simple games in the Looney Labs vein, (dare I say, Fluchtpunkt games?) I appreciate the games included in the book.  Not only are they informative, but they're also fun to play.

[cb]: http://landoflisp.com/

[joy]: http://www.joyofclojure.com


# Fun

> These things are fun, and fun is good.
>  Dr. Seuss

This section contains odd-ball entries that do not fit anywhere else.  All bets are off for strict adherence to the theme.  The only constant herein is that you shouldn't take things too seriously.

## Voices from the Apple

Apple once had a brilliant marketing campaign famously known as "Wheels for the mind."  The starkly simple, yet powerful image that went along with that phrase was as follows:

![Wheels for the Mind](http://readevalprintlove.fogus.me/images/wftm.jpg)

This particular ad was run in 1981 and referred directly to the [Apple II line of computers](http://apple2history.org/).  However, even after that ad ran its course the company designed and developed amazing technologies that truly did serve as "wheels for the mind," including, but not limited to the following.

### Macintosh Common Lisp (MCL)

<ftp://ftp.informatimago.com/pub/lisp/macintosh-common-lisp-reference.pdf> (PDF)

MCL is/was a standards-compliant version of Common Lisp with a very powerful IDE for creating Macintosh applications.

### Hypercard 

<http://hypercard.org/>

An early hypermedia development language and platform that was a revelation for many people who used it.  With a little extra context here and perhaps a little luck there, Hypercard might have served as the basis for the World Wide Web, rather than simply an inspiration.  As it stands, it's commonly believed that the direction of the WWW in contrast to Hypercard's limited viewpoint was its downfall.  However, Stanislav Datskovskiy [^why-die] makes a different case altogether -- one that you'll more fully understand at the punchline of this segment.

[^why-die]: http://www.loper-os.org/?p=568

### Dylan 

<http://opendylan.org/>

Dylan is a Lisp-like object-oriented programming language originally designed as a [Newton](http://oldcomputers.net/apple-newton.html) development system.  While Dylan is still actively maintained and used, it's ongoing evolution was divorced from Apple long ago.

These languages were, and are, amazing and important entries in the annals of langdev -- so is it any surprise that they found their start at Apple?  Probably not. However, that they've been allow to die and been excised from their roots is sad, but perhaps not too surprising given the direction of Apple products over the past ~10 years.

### Wheels of a sort

Each of the languages listed above were ahead of their time and offered first-class development environments for the Apple line of computers and systems.  However, over time Apple eventually phased out each and every one and indeed the very computers that they targetted.  From the start, the Apple I and early versions of the Apple II computers were software and hardware extensible and for many a young man or woman were truly "wheels for the mind."  

Sadly, had Apple simply phased out old hardware and development systems in favor of something new and more powerful then few would have shed a tear.  Instead, Apple moved away from the very notion of "wheels of the mind" in favor of building systems for consumers.  Objective C, the iPad and iCloud are no longer "wheels for the mind" but are instead simply "training wheels for the mind."

![Training wheels for the mind](http://readevalprintlove.fogus.me/images/twftm.jpg)

Tools for getting a job done.

Tools for viewing trivialities.

Tools for tools?

## Matters of perspective

The long-standing trench-warfare between Common Lispers and Schemers has claimed many a pride as casualties.  While the "soldiers" have grown weary over the years, the fundamental differences between the two camps can be summarized as in the following relativistic lexicon.

| Term                  | Common Lisp                                             | Scheme                      |
|-----------------------|---------------------------------------------------------|-----------------------------|
| Hygiene[^flet]        | Always use earmuffs and wisely use `FLET` and `LABELS`   | Macros, the Scheme way      |
| proper tail-calls     | Function with no bugs having calls in the tail position | *no definition*             |
| Proper Tail-Calls     | *no definition*                                         | Tail-calls, the Scheme way  |
| Tail-call elimination | A vendor-specific feature                               | Porting SCM code to CL      |
| Higher-order thinking | Remembering to use `#'`                                 | Remembering to use Scheme   |
| Higher-order function | One taking or returning other functions                 | The conceptual Maginot Line |
| Lisp-1                | The index entry before Lisp-2                           | The definition of beauty    |
| Lisp-2                | The index entry before Lisp-3                           | The definition of ugly      |

[^flet]: I understand how packages and the restrictions on the core symbols help here -- let me have some fun please.


## Links, source, posts, pictures, papers, music and more

 * (BOOK) [Land of Lisp by Conrad Barski](http://www.amazon.com/dp/1593272812/?tag=fogus-20)
 * (BOOK) [The T manual](http://repository.readscheme.org/ftp/papers/t_manual.pdf) by Rees, Adams, and Meehan (PDF)
 * (BOOK) [Simply Scheme: Introducing Computer Science](http://www.cs.berkeley.edu/~bh/ss-toc2.html) by Brian Harvey and Matthew Wright

 * (CODE) [Javascript compiler for EmacsLisp](https://github.com/nicferrier/emacs-ejit) by Nic Ferrier
 * (CODE) [A teeny-tiny Markdown parser in Clojure](https://github.
 * (CODE) [Lane Detection using Clojure and OpenCV](http://nakkaya.com/2011/01/24/lane-detection-using-clojure-and-opencv/)

 * (MUSIC) [Bow Echoes by Damian Valles](http://www.restingbell.net/releases/rb081-bow-echoes)
 
 * (PAPER) *Advanced Programming Language Features for Executable Design Patterns: Better Patterns Through Reflection* by Gregory T. Sullivan

 * (TUTORIAL) [GregHendershott's Fear of Macros](http://www.greghendershott.com/fear-of-macros/)
com/chameco/Hitman/blob/master/src/hitman/core.clj)
 * (TUTORIAL) [Emacs Lisp Examples](http://ergoemacs.org/emacs/elisp_examples.html) by Xah Lee


# Finally

If you've enjoyed this installment of Read-Eval-Print-λove then please consider buying the PDF / mobi / epub versions on Leanpub at <https://leanpub.com/readevalprintlove001>, paying whatever you think it's worth.

I'd like to thank Xach Beane for the AutoMotivator webapp used to create the Erik Naggum image and Conrad Barski for the "Alien technology" images.  I'd also like to thank Craig Andera and Russ Olsen for reviewing a draft of this issue.  Also, Read-Eval-Print-λove's spirit is inspired by the beautiful works of Kragen Javier Sitaker.  Finally, the cover of this issue was painted by my mother-in-law Kiyomi Okada.

Is there something that you'd like to see in future issues?  Email me at the address below with suggestions.  If you'd like to discuss this issue of Read-Eval-Print-λove then head on over to <http://www.lispforum.com> or the LL.next mailing list at <https://groups.google.com/forum/#!forum/ll-next> -- I'll be there.

The tentative release date for issue #2 is sometime in late October or early November, 2013.  The theme for issue #2 is "Orientation around objects."


# Author information and links

[Michael Fogus](http://www.fogus.me) — a core contributor to
[Clojure](http://www.clojure.org) and [ClojureScript](http://www.clojurescript.net).  Creator of [programming source codes](https://www.github.com/fogus).

A fervent blogger at [Send More Paramedics](http://blog.fogus.me) and also
co-author of the book, *[The Joy of Clojure](http://www.joyofclojure.com)* and author of *[Functional JavaScript](http://www.functionaljavascript.com)*.

**Author contact**

* <http://www.fogus.me>
* <http://www.twitter.com/fogus>
* <https://www.github.com/fogus>
* me -at- fogus -dot- me

**Discussion and information**

* <http://www.readevalprintlove.org>
* <https://www.github.com/readevalprintlove>
* <http://www.lispforum.com/>
* <https://groups.google.com/forum/#!forum/ll-next>


