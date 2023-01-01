It seems that if a resource was cached in "resources/_gen" it will appear in "public" even if publishResources = false and there are no permalinks to that resource.

Tested in version `hugo v0.109.0-47b12b83e636224e5e601813ff3e6790c191e371 windows/amd64 BuildDate=2022-12-23T10:38:11Z VendorInfo=gohugoio`.

Reproduce steps:
1. clean directories `public` and `resources`
2. run `hugo`
3. directory `public/page` contains `index.html`, `test.jpg`
4. run `hugo`
5. directory `public/page` now contains `index.html`, `test.jpg`, `test_hu360497c2a11d6b503ab55b11082e86dd_9951_100x100_fit_q75_box.jpg`

I believe that file `test_hu360497c2a11d6b503ab55b11082e86dd_9951_100x100_fit_q75_box.jpg` should not appear because there are no permalinks to it.

And I believe that two consecutive launches of `hugo` should give the same result in `public`.
