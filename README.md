# SqueakNews

SqueakNews was an e-zine devoted to [Squeak Smalltalk](https://squeak.org) created and published in 2001 by Tansel Ersavas, with collaboration by many members of the Squeak community. It may be considered the pinnacle achievement of the Squeak community at its finest hour.

It is still the best example of Active Essays, and the closest to a Dynabook.

A live version is hosted on Dan Ingalls' Smalltalk Zoo site:

https://smalltalkzoo.computerhistory.org/SqueakNews/index.html

It is mentioned in Dan's HOPL paper:

https://smalltalkzoo.computerhistory.org/papers/EvolutionOfSmalltalk.pdf

## Original distribution

SqueakNews e-zine issues originally were distributed on CD-ROM. The ISO images are in Tansel's repo:

https://github.com/tansel/SqueakNews

These issues include 32 bit Squeak VMs, which may still run if your system supports 32 bit executables.

## This distribution

The distribution in this repository makes the issues viewable in a web browser using [SqueakJS](https://github.com/codefrau/SqueakJS). This web player was initially created by Vanessa Freudenberg during the plague of 2020.

It includes five directories, one per issue. Each issue's files were copied directly from the corresponding ISO image. The files are unmodified. VM files were excluded.

We added an index page with the table of contents of each issue, which was scraped from the table of contents project in each issue.

## Technical

Each issue has a 32 bit image in the original Squeak interpreter format named `ezine.image`, and a directory of image segments in the `ezine-segs` directory. Each article is in its own project, which is stored as a separate image segment file. Image segments are loaded into memory automatically when entering each project.

In this version, the segment files are fetched on demand using SqueakJS's templating mechanism. Each directory has a `sqindex.json` file created by running [mkindex](https://github.com/codefrau/SqueakJS/blob/main/utils/mksqindex.py).

## Peeking behind the scenes

The Ezine images are configured to use simplified menus and halos. They are otherwise full Squeak images.

Open the "Juggle With Squeak" project to get the regular Squeak world menu with full access to development tools.

Modify `EzineEntryMorph>>hijackMenus` to allow full menus in any project.

Execute `Preferences resetHaloSpecifications` to get the default Morphic halo handles back.

## Contributing

Contributions to the HTML / Javascript parts are very welcome. In particular, the CSS/HTML could be a lot prettier, especially on mobile devices.

The Squeak parts are historical artefacts and should not be touched much. Then again, if little tweaks would make e.g. navigating in a web browser significantly more enjoyable, we should consider that. For example, being able to scroll using a mouse wheel or dragging would be very nice. Adding new issues would be awesome, of course.

Also, some things are not yet working correctly. E.g. the MP3 audio player and MPEG video player in issue 3, or the Celeste mail archive in issue 5. These will probably have to be fixed in [SqueakJS](https://github.com/codefrau/SqueakJS). The `squeak_bundled.js` file here is a copy of the one in `SqueakJS/dist`. Rebuild it using `npm run build:bundle`.

Please [report](https://github.com/squeak-smalltalk/squeaknews/issues) problems you find! And help fixing them is appreciated too, of course.

See the [Squeak Community](https://squeak.org/community/) page for other options to get in touch with us.
