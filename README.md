# uppy

A work in progress - nothing to see here.

Interesting places if you want to dig in:

 - Architecture in [`website/src/api/index.md`](https://github.com/transloadit/uppy/blob/master/website/src/api/index.md)
 - Contributor's guide in [`website/src/guide/contributing.md`](https://github.com/transloadit/uppy/blob/master/src/guide/contributing.md)
 - [Open issues](https://github.com/transloadit/uppy/milestones/Minimum%20Viable%20Product) before having a Minimum Valuable Product. 

## Uppy Development

First clone and install the project:

```bash
git clone git@github.com:transloadit/uppy.git
cd uppy
npm install
```

Our website's examples section is also our playground. To get it to run locally type:

```bash
make website-preview
```

## Website Development

We keep the [uppyjs.io](http://uppyjs.io) website in `./website` for so it's easy to keep docs & code in sync as we're still iterating at high velocity. For those reading this screaming murder, [HashiCorp does this](https://github.com/hashicorp/terraform/tree/master/website) for all their projects, and it's working well for them on a scale vastly more impressive than :dog:'s.

The site is built with [Hexo](http://hexo.io/), and Travis automatically deploys this onto GitHub Pages (it overwrites the [`gh-pages`](https://github.com/transloadit/uppy/tree/gh-pages) branch at every deploy).

Content is written in Markdown and located in [`./website/src`](https://github.com/transloadit/uppy/tree/master/website/src). Feel free to fork & hack!  

`./website/update.js` is called during website builds to inject the Uppy versions & filesizes into the documentation. `website` in an independent folder (with e.g. its own package.json) and so it cannot rely on anything from the root project directly. `update.js` is the bridge that explicitly makes information available by injecting it into the website.

It's recommended to exclude `./website/public/` from your editor if you want efficient searches.

For local previews on http://127.0.0.1:4000 type:

```bash
make website-preview
```

## FAQ

### Why does your site look like vuejs.org?

The website is currently a clone of Yuxi Evan You's wonderful [Vue.js](http://vuejs.org/) website ([view license](website/VUEORG_LICENSE)) - just so we can hit the ground running in terms of Haxo boilerplate, etc. Obviously as soon as possible, we'll start rolling out our own layout & content and make this place our own. We'll keep the Vue website MIT license & credit in the footer in tact of course.

### What does Travis do?

Travis should:

- [x] check out code 
- [x] build project
- [ ] run unit tests
- [ ] run acceptance tests
- [x] copy/install the built project into any `examples/*/`
- [x] deploy the examples to our hackathon S3 bucket in a folder named by branch (http://hackathon.transloadit.com/uppy/master/index.html), so we can all play with the current state of the project & examples per branch, without installing everything locally.
