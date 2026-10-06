# Coding bootcamp fees in India — open dataset

Fees, durations, formats and batch start dates for **85 bootcamp and professional
certification programmes across 16 training institutes in India**, read off each
institute's own public course pages.

Every row carries the `source_url` it was read from, so any figure can be checked
against the institute's own page.

Maintained by [BootcampGuide](https://www.bootcampguide.com). Updated monthly.

## Why this exists

There is no public, structured record of what technical training actually costs in
India. Fees are scattered across hundreds of marketing pages, frequently absent,
and quoted differently depending on who is asking. This dataset is an attempt at a
checkable baseline.

## Headline findings

| | |
|---|---|
| Programmes covered | 85 across 16 institutes |
| **Publish both a fee and a start date** | **42 (49%)** |
| Publish a fee | 67 (79%) |
| Publish a start date | 55 (65%) |
| Median published fee | ₹85,000 |
| Middle half of fees | ₹54,000 – ₹140,000 |
| Full fee range | ₹12,900 – ₹399,000 |
| Median cost per month of tuition | ₹12,143 |
| Cost per month range | ₹4,000 – ₹49,667 (**12x**) |

**Only 49% of programmes publish both a price and a start date.** For the other half, a
prospective student cannot answer the two most basic questions about a programme
without entering a sales process.

IIDE and Craw Security publish no fee on any of their courses. upGrad, Coding Ninjas, GeeksforGeeks, AccioJob and Imarticus Learning publish no start date on any of theirs.
In every case the programmes are real and enrolling — the information is simply not
on the page.

On comparing fees: the ₹12,900–₹399,000 total range is not a like-for-like difference. The
bottom is self-paced video; the top is a twelve-month live programme. Cost per
month of stated tuition is the fairer comparison, and it still spans 12x.

## Files

| File | Rows | Contents |
|---|---|---|
| `data/courses.csv` | 85 | One row per programme, 18 columns |
| `data/courses.json` | 85 | Same, with retrieval date and licence |
| `data/institutes.csv` | 16 | One row per institute |

## Columns

| Column | Notes |
|---|---|
| `institute`, `institute_slug`, `institute_hq` | Provider and its head office |
| `course_name`, `specialisations`, `level` | As the institute names them |
| `format` | `Online`, `Offline` or `Hybrid` |
| `online_mode` | `Live` or `Self-paced`; empty for non-online |
| `centres` | `city, state`, semicolon separated; empty for online-only |
| `duration` | Verbatim, e.g. `6 months`, `6 - 8 Months`, `16 weeks` |
| `fee_inr` | Integer rupees as published. **Empty means not published, never zero** |
| `fee_published` | `yes` / `no` — makes the absence countable |
| `emi_available` | `yes` / `no` |
| `total_seats` | Empty unless the institute states it |
| `next_batch_1`, `next_batch_2` | ISO 8601. `2026-10-24` when the day is known, `2026-10` when only the month is |
| `batch_date_published` | `yes` / `no` |
| `source_url` | The page the row was read from |

`fee_published` and `batch_date_published` exist so you can measure what is missing
without inferring it from empty cells.

## Methodology

- Figures come from each institute's own public course pages — not brochures, sales
  calls, or third-party aggregators.
- Institute and course details captured **19 September 2026**; every batch date
  re-verified against the live course page on **7 October 2026**.
- **Nothing is inferred, estimated, converted or filled in.** Where a value is not
  published, the cell is empty and the corresponding `*_published` column says `no`.
- Fees are as published and may exclude GST where the institute presents them that
  way. They are not normalised.
- Durations are verbatim. Ranges like `6 - 8 Months` are left as written; any
  midpoint arithmetic is the consumer's choice, not baked in.
- Pages that quoted a fee in a non-rupee currency because of geographic pricing were
  excluded rather than converted.
- Programmes whose source pages have gone offline are removed rather than carried
  forward on stale data.

### Known limitations

- Two institutes render their batch tables client-side, so their dates read as
  unpublished here even though dates may exist on the page.
- Institutes that price by salary band after placement rather than up front do not
  reduce to a single `fee_inr`.
- Coverage is the 16 institutes BootcampGuide tracks, not a census of the Indian
  market. It skews toward larger, national providers.

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Free to use, share and
adapt, including commercially, with attribution.

Suggested citation:

> BootcampGuide, *Coding bootcamp fees in India* (85 programmes, 16 institutes),
> October 2026. https://www.bootcampguide.com/blog/coding-bootcamp-fees-india

## Corrections

If you run one of these institutes and a figure is wrong, open an issue. Every row
carries the `source_url` it was read from, which makes disagreements quick to settle.
We would rather fix a number than defend it.
