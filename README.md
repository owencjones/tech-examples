# Tech Examples <!-- omit in toc -->

## A collection of curated examples of work I've done with brief explanations to show to anyone interested <!-- omit in toc -->

This repo includes a group of different examples of code, in various languages (mainly Javascript and Python), and brief one-line explanations of each.  The examples include:

- Production code, written for actual projects
- Tech Tests
- Pretty quick and hacky tooling code and utilities
- Academically interesting examples of Computer Science related concepts

- [Production code examples](#production-code-examples)
  - [Office for National Statistics, Response Operations UI](#office-for-national-statistics-response-operations-ui)
  - [Office for National Statistics, RAS Frontstage](#office-for-national-statistics-ras-frontstage)
- [Technical Tests](#technical-tests)
  - [Identify the background colour of an image](#identify-the-background-colour-of-an-image)
  - [Restaurant Listings Test](#restaurant-listings-test)
- [Tooling and scripts](#tooling-and-scripts)
  - [PartyHammer](#partyhammer)
- [Academic code examples](#academic-code-examples)
  - [JSQuine](#jsquine)
  - [Euler in C](#euler-in-c)

### Production code examples

#### [Office for National Statistics, Response Operations UI](https://cutt.ly/HwsthGc)

Response operations UI is an internal ONS system for dealing with the responses people make online to surveys the ONS sends to them.  Written in Python, HTML, and Javascript.

Link goes to a list of pull requests of mine, so my actual code.

#### [Office for National Statistics, RAS Frontstage](https://cutt.ly/AwstRgM)

RAS Frontstage is the ONS' online survey platform, public facing.  Also written in Python, HTML, and Javascript.

Link goes to a list of pull requests of mine, so my actual code.

### Technical Tests

#### [Identify the background colour of an image](https://bitbucket.org/seajones/imagecheck/)

A technical test for a previous job, the task was to work out the background colour of a given image from those in a palette.  It's a working solution, but it was not done with tests, as it would be live.

#### [Restaurant Listings Test](https://bitbucket.org/seajones/kukd-tech-test)

This was a tech test sprung on me at the end of an interview.  It took 6 hours to do, and the company involved expected me to stay on premises to do it, so the solution works, but is a little rough and ready.  I was ultimately offered the job, but declined.  The solution was written a few years ago, so uses older Javascript paradigms.

### Tooling and scripts

#### [PartyHammer](https://github.com/owencjones/partyhammer)

PartyHammer was a tool for testing an API I was finding troublesome before we were able to get an environment to work in.  It hits the API with batches of different requests, randomised data, and at various intervals, and produces raw data for analysis.

Also includes a tool that produces metrics in Markdown format for use.

It was a quick and hacky script to make, so it lacks production features like tests.

### Academic code examples

#### [JSQuine](https://github.com/owencjones/jsquine)

A Quine is a program that outputs its own source code.  Of no real use, it's an exercise in understanding a language, and also a test of turing completeness, I wrote two in this repo (one worked but I consider it a bit of a cheat, so I wrote another), along with a simple test to ensure each worked.  It runs in Node, and should work with most versions.

#### [Euler in C](https://github.com/owencjones/Euler-C)

Project Euler is a large set of problems to solve in code, and this repo is one I've been returning to now and again with further solutions to one or more of the hundreds available.  Each is designed to have a naive solution, but can be improved by application of Computer Science and Mathematical principles.  I've done the first seven currently, and I add one here an there when I get chance.

Looking at the commit history is useful on this, as I start with naive solutions and then look for the improvement opportunities.  One example is below:

```c
int is_prime(int num)
{
     if (num % 2 == 0 && num > 2) return 0;
     for(int i = 3; i < num / 2; i+= 2)
     {
         if (num % i == 0)
             return 0;
     }
     return 1;
}
```

The naive approach to detecting if a number is prime is dividing it by every number from 2 to itself minus one, this makes some improvements on this:

- The function finishes early if the number is even and over 2, because an even number over two is not prime - saves time when iterating.
- The function starts iterating at 3, because every integer divides by one, and we already know 2 isn't prime, and 2 is.
- The function iterates in twos because even numbers are not prime, except 2, which is already covered.
- The function divides each check by 2, halving the tested number each time, which is a sieve approach.  This massively reduces the number of numbers tested.  This is because if a number under test is not a factor so far, you can skip next to half of that number.  The numbers in between will not be factors.
