# OONI Software Style Guide

The purpose of this repository is to collect all style related documentation
and guidelines for OONI related projects.

At OONI we write a bunch of software in a variety of different languages. Here
we document the style we follow for each language.

## General

### Versioning

All projects under the OONI umbrella should follow [semantic
versioning](http://semver.org/), this means the version string should follow
the pattern `MAJOR.MINOR.PATCH` (or `MAJOR.MINOR.PATCH-(beta|alpha|rc)(.N)(+BUILD_ID)`)

`BUILD_ID`, when optionally specified (for example on mobile platforms), should always be increasing.
That is to say `∀ n ∈ ℕ : BUILD_ID(n) > BUILD_ID(n-1)`.

Example of good version numbers:

```
1.1.2
3.2.0-rc.0
1.34.22-beta.36
2.0.0-rc.1+233
```

Example of **BAD** version numbers:

```
1.1
2.0.2-rc
1.2.1.beta
2-beta.3
3.2.1-rc-1
3.3.3.3
```

### Tagging

When tagging a release all you have to do is call the tag with the version
number with a leading `v`.

For example if the version number of the software is `2.8.1`, the tag will be
labeled `v2.8.1`.

If you are making an alpha, beta or release candiate be sure to always include
the `-rc.1` or `-beta.1` suffix.

If you are on mobile be sure to append the build ID to the tag using the format `+N`.

The message (or annotation) for the tag should be in the format:

```
SOFTWARE_NAME MAJOR.MINOR.PATCH
```

For example if your software is called `ooniprobe` and the version is `1.1.2`,
the annoation will be:

```
ooniprobe 1.1.2
```

You can optionally include a summary of the changelog after the second line.

Examples of bad tags:

```
tag name: v1.1.2
tag annotation: mysoftware v1.1.2
```

```
tag name: 1.1.2
tag annotation: mysoftware 1.1.2
```

```
tag name: v1.1.2
tag annotation: 1.1.2 mysoftware
```

```
tag name: v1.1.2
tag annotation: mysoftware (1.1.2)
```

### Changelog

A Changelog file should be present in the root of every repository and lists
changes added to every release of the software.
This file should be called `ChangeLog.EXT` where `EXT` should be preferrable
`md` (for markdown), but can also be `rst` or `txt` in special cases.

Changelog entries are important, it's how we comunicate to our users what
exciting new features or important bugs we have fixed in this flashy new
release. Take your time when writing them.

[Keep a changelog](http://keepachangelog.com/en/1.0.0/) has some useful tips on
writing good changelogs.

The entries in the changelog should be sorted from most recent to most old (the
bottom of the file will contain the first ever release).

Each entry should have the following structure:

```
<Heading level=1>ChangeLog</Heading>

<Heading level=2>SOFTWARE_NAME VERSION_NUMBER [TIMESTAMP]</Heading>

Some top level summary

Added:
<List>
  <Item>This feature was added</Item>
</List>

Changed:
<List>
  <Item>This functionality was changed</Item>
</List>

Deprecated:
<List>
  <Item>This feature will soon be removed</Item>
</List>

Removed:
<List>
  <Item>This feature was removed</Item>
</List>

Fixed:
<List>
  <Item>This bug was fixed</Item>
</List>

Security:
<List>
  <Item>OMG there was a security issue</Item>
</List>
```

`TIMESTAMP` must be the ISO timestamp (ex. `2017-09-08`).

The sections can be omitted if nothing relevant is to be included in them.

### Releases

When you make a binary release be sure to always include the version number in
the filename you upload.

If you are uploading a release to test flight or other distribution channels, you
must create a tag before doing so. Every release pushed to any distribution channel
must have a corresponding git tag.

If you are making a beta or unstable release, be sure to comunicate this
adequately when you distribute it.

### Naming projects

> There are only two hard things in Computer Science: cache invalidation and naming things.
> - Phil Karlton

Since recently we have started to loosely have more consistency in naming
software projects.

If you are to start some new OONI related project, you should name the software
project with a Marine themed name.

This can include, but is not necessarily limited to, the following:

* [The name of a fish](https://en.wikipedia.org/wiki/List_of_common_fish_names)

* [A sea god](https://en.wikipedia.org/wiki/List_of_water_deities)

* [Marine life](http://oceana.org/marine-life)

* [A legendary sea creature](https://en.wikipedia.org/wiki/List_of_legendary_creatures_by_type#Aquatic_and_marine_mammals)

## Language specific

### Python

Refer to [coding-style in the ooniprobe
repository](https://github.com/TheTorProject/ooni-probe/blob/master/docs/coding-style.md).

### Javascript

We follow [Javascript Standard Style](https://standardjs.com/)

### Golang

Refer to [Effective Go](https://golang.org/doc/effective_go.html). `go fmt` and `go lint` will also be of help.

### C++

Refer to [coding-style in measurement-kit](https://github.com/measurement-kit/measurement-kit/blob/master/doc/coding-style.md)


