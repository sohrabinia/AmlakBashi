# Amlakbashi Public Live — Checkpoint 2026-10-07

This checkpoint records the verified work completed on Public Live before continuing the remaining smoke tests.

## Verified fixes

- Stale Region cache was identified as the root cause of the broken `/s/2/تهران` result. Cache key `Category_Item_55784` was invalidated; the route immediately returned 12 listings with a correct canonical.
- Seven main regional routes were tested and reported as `200 + 12 listings + canonical`.
- Production-side source changes were synchronized toward GitHub; the working changes were intended to become the new source-of-truth checkpoint.
- Issue #44 was used as the tracking reference for the URL/photo investigation.
- Listing/card image endpoints tested during the audit returned real HTTP 200 responses for the sampled records.
- 285 Published+Available listings were found without PhotoID and AlbumPhoto; Legacy showed essentially the same state, so no fabricated PhotoID mappings were applied.
- Of 11 records with AlbumPhoto but PhotoID=0, only listings 97703 and 97705 had verified original image files available in backup.
- Listing 97703 was recovered with PhotoID 277751.
- Listing 97705 was recovered with PhotoID 277783.
- Original images and real thumbnails for both recovered listings were restored, and their image endpoints plus detail-page gallery/og:image markup were verified.
- Backup inspection did not find a valid media source for the remaining cases examined.

## Important remaining status

The site must NOT yet be declared fully complete. The final Home/Category/Detail smoke test and the remaining URL/photo validation still need to be completed.

## Working rule from this checkpoint

Continue all further fixes from this Git checkpoint. Do not overwrite or discard the verified state. Any subsequent production change must be reflected back into Git before it is considered part of the source of truth.
