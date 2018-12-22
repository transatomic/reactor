These instructions are also at [https://transatomic.github.io/maintenance.md](https://transatomic.github.io/maintenance.md).



<br/><br/>

# Maintenance

Maintaining this site is easy.  It's a [github pages](https://pages.github.com/) site.

This site currently relies on Github's mechanism to translate `markdown` to HTML.  That
is not required, and may be disabled at any time.



<br/><br/>

## Updating the page

Updating is done with an `npm` script in `package.json`.

```
npm update
```

The site will now rebuild itself.  Afterwards, just commit as normal.

```
git add . -A
git commit -m "what changed"
git push origin
```

Given a minute or two, the site will now update itself.



<br/><br/>

## Changing the theme

Because of the `npm` automation, there's an extra step to changing the theme, above and
beyond a normal Github Pages site.  (Sorry.  It's fixable, but I'm lazy, and theme changing
is something most people do zero or one times, so, it doesn't seem worth the effort.)

1. First update the theme like you'd expect. Notice that it works. 
    1. Ha! This is software. 
    1. It will fail later when you don't expect it and don't remember the relevant context.
1. Later, you update the docs and rebuild. 
    1. Wtf? The. The old theme is back?
1. That's because of a step at the end in `package.json` 
    1. This step copies its clone of the gh pages config, which includes theme, over the existing one
    1. That's because nuking the docs folder nukes the gh pages config
1. So if you want to change the theme:
    1. Make the change as normal
    1. Pull the repo. 
        1. Notice GH has changed `/docs/_config.yml`
    1. Replace the repo's `githubpages_config.yml` with that new `_config.yml`
    1. Now the build process enforces your new theme instead of the old one
    1. Huzzah