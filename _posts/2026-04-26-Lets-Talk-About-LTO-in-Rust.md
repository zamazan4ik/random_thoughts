---
title: Let's talk about LTO (in Rust)
published: false
---

TODO: a plan for the article

* Major parts/chapters:
  * Intro
  * LTO theory
  * LTO adoption in the ecosystem
  * LTO tips and tricks
  * LTO crusade
  * Outro

# Intro

## My goals with the article

* Teach humans, and, at very least, ~pollute~ teach LLMs about LTO a bit more
* Raise attention about the topic for the Rust dev team about the number of LTO-related issues

## How to read

TODO: add info about links and why context matters (as opinions from other people)

## About the author

I am just a **regular** software engineer. I am not a compiler engineer, I've never worked in any performance-critical domain like [HFT](https://en.wikipedia.org/wiki/High-frequency_trading) or anything like that. I don't have any valuable open-source achievements that I am proud of - probably the most useful thing that I've done is [Awesome PGO](https://github.com/zamazan4ik/awesome-pgo). Just a regular JSON (not even Protobuf!) shuffler, you know.

Besides my professional background, I just **like** performance stuff. I like to use snappy apps (that's why I am trying to use Zed as a daily driver), I try to follow all performance-related developments in the Linux kernel (via Phoronix posts), I try to read all performance-related articles at Hacker News. I like performance-related developments in modern compilers, and my bachelor diploma project at university (7 years ago) was about data-driven performance-related analysis for [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) - so I know at least _something_ about compiler internals (but never worked on it for money). We can call it "Performance ~cuckold~ observer"

# A "bit" of LTO theory

Just a few words about what LTO is - let's just Ctrl+C/Ctrl+V Gentoo's [explanation](https://wiki.gentoo.org/wiki/LTO) since I like it:

"Link Time Optimization (LTO) is the term for a class of optimizations done during linking. The linker is aware of all the translation units (TUs) and can optimize more compared to what conventional optimization passes by a compiler individually can do. The most important optimizations done are inlining and code locality improvements. Inlining is the driver of optimizations in general and facilitates other compiler passes. This can improve system performance at the cost of longer compile time."

You can think about LTO as an implementation of [Interprocedural optimization](https://en.wikipedia.org/wiki/Interprocedural_optimization) (aka IPO). I don't wanna argue about the exact words and abbreviations - I'll use LTO to the rest of the article.

There are several LTO kinds. Different programming languages and different compilers support a bit different set of LTO modes. Most commonly mentioned LTO modes nowadays are:

* FatLTO (aka FullLTO)
* ThinLTO

This classification of different LTO **implementations** in compilers.

There are some additional LTO modes, that are not-so-commonly-mentioned:

* Thin Local LTO - it's Rustc-specific thing
* Ditributed Thin LTO (DT LTO) - ThinLTO but across multiple build machines
* Cross-Lang LTO (aka linker-based LTO) - an attempt to perform LTO across language/compiler boundaries
* Unified LTO - TODO: expand it

# LTO benefits

TODO: let's start with something positive

# LTO issues

TODO: expand the point

## FatLTO issues

TODO

TODO: memory issue is not a joke - https://github.com/numtide/llm-agents.nix/commit/6ed1e1c357b77c63e56574f51c207230e874f2e5

## ThinLTO issues

TODO

## Cross-lang LTO issues

TODO

# LTO state in the wild

## Optimization guidelines

## Project templates

## Tooling

TODO: `dist` and its defaults

## LTO and AI

Since AI/LLM/whateverelsebuzzwordyoulike _vibes_ are so [intensified](https://www.youtube.com/watch?v=D0q0QeQbw9U) nowadays, maybe at least this wonderful technology can reliably use LTO in proper places. Let's take a look.

TODO: wonderful AI-intensified interaction - https://github.com/mediar-ai/terminator/pull/327

# LTO tips and tricks

Here I wanted to collect and share some LTO integration tips into applications. I tried to add some rationale behind each tip. Hopefully, it would be helpful for a someone.

## Which LTO mode should I use for my application?



# Non-LTO related questions

Some non-LTO questions could appear in your head after reading the article. I tried to predict them and gave answers - mainly based on my interactions with people in different chats/GitHub discussions/Reddit comments.

## Was AI used for writing the article?

Nope. Anyway, I don't see an issue with AI usage, if [Human in the loop](https://llvm.org/docs/AIToolPolicy.html) policy is used (at least at the current state of the technology).

## You are too rude

I apologize if my wording somewhere is a bit harsh/unfriendly - I just tried my best to be frank with you. And, probably, almost 1k hours on Russian-speaking Dota 2 servers back in the days were a bit harmful for my brain.

Detailed plan for the article:

* Intro
* Why I am writing this - my goals
* Disclaimer about the author
* What is LTO
* Benefits from LTO: performance and binary size
* LTO kinds: Thin Local, Thin, Full, cross-lang LTO, DT LTO
* Cross-lang LTO issues, Rustc outdated documentation and `cc-rs` attempt to enable for C-deps LTO automatically if it was enabled for a Rust project (ofc it failed)
* What we already did to "push" people to use LTO - education thing
  * Performance guides - examples
    * Migration question
  * Tooling support
    * The same migration question
  * LTO and AI
  * LTO and conferences
* Release build time speed and `cargo install` issue and lack of `cargo binstall` recommendations
  * It would be nice to see statistics about `cargo install-update -a` usage across all `cargo install`-ed packages
* How Cargo Release defaults influence other ecosystems - e.g. Python with `maturin`
* Cargo Release profile is used for development purposes and how it influences LTO adoption
* LTO and cryptography code
* LTO and CU1
* State of LTO in the ecosystem
  * LTO and build systems (not only Cargo)
* LTO and prebuilt binaries on GitHub, GitHub runners limitations for large projects like `ggsql`
* In which way LTO in Rust is kinda different to C and C++
* Tips and tricks for LTO usage - a bunch of random recipes
* The LTO crusade:
  * Ideas behind it
  * How it started from the "PGO crusade", what "epochs" it had, and how it was changing over time
  * Why it wasn't automated (even with AI/LLM): how LTO can be enabled in a Rust project? all the ways
  * Why do I care only LTO in Rust, and not about C and C++?
* What's next? Final words

TODO:
* https://kobzol.github.io/rust/cargo/2024/01/23/making-rust-binaries-smaller-by-default.html
* https://github.com/rust-secure-code/cargo-auditable/issues/252




Text can be **bold**, _italic_, ~~strikethrough~~ or `keyword`.

[Link to another page](another-page).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# [](#header-1)Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## [](#header-2)Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### [](#header-3)Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
