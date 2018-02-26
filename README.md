# HSTS-SuperCookie
Storing data as HSTS super-cookies is a topic that has come up several times in the past. This simple HTML file along with proper setup with nginx demonstrates that, thankfully, this is no longer an issue, since most major browsers now use separate HSTS sets for incognito modes.

## Demo
A demo found [here](http://demo.hsts.radialapps.com/demo/supercookie.html) was working as of writing this! If you set some data, it should be accessible after you refresh the page, but will vanish if you open incognito/private mode.

## Working
The client makes JSONP requests to nginx, which responds with 1 if https was used to call the request, and 0 if not. The client can set the data by calling `https://URL/set`, which will return the HSTS header. This data is then read to make some sense out of it.

## Background
At the time I write this, [Wikipedia noted](https://en.wikipedia.org/w/index.php?title=HTTP_Strict_Transport_Security&oldid=824540810#Privacy_issues) that HSTS can potentially have privacy issues, with HSTS being enabled being possibly used as a store of super-cookies. While I could find references that it had been fixed in most browsers that incognito modes used a different HSTS set, I just had to be sure!