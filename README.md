# Proxy seller: how to spot a fair per-GB price, test any vendor in 24 hours, and where DataImpulse's $1/GB pay-as-you-go fits

"Proxy seller" is two searches wearing one coat.

One is a brand search: there is a company literally called Proxy-Seller, and people looking for its pricing page type those two words. If that's you, this article still helps, because the way to judge that vendor is the same way you judge every other one. The other search is the broad one: someone wants to buy proxies, has no particular seller in mind, and is trying to work out what "reasonable" looks like before they hand over a card number.

That second reader is annoying to write for, because the proxy market is deliberately hard to compare. Two vendors quote "from $1 per GB" and one of them charges you double that the moment you target a city. Another sells you 50 GB that quietly expires in 30 days if your scraper has a slow quarter. The sticker price is real, but it's the least important number on the page.

So here's what actually decides whether a proxy seller is worth your money, and where DataImpulse fits into that picture.

## Four ways proxy sellers bill you, and where the markup hides

Almost every vendor uses one of four models, and they're not interchangeable.

**Per GB.** You pay for data that moves through the proxy. This is standard for residential and mobile pools, because the value is the quality of the IP, not any specific endpoint. Easy to predict if your traffic is steady, brutal if you accidentally point a video downloader at it.

**Per IP or per port.** You rent specific addresses for a fixed period, usually a month. Common with datacenter and static ISP proxies, where you want an address that stays yours. Unlimited traffic is often bundled in, which makes it look generous until you notice the per-IP rate.

**Subscription.** A recurring monthly package with a traffic allowance. Vendors like it because it's predictable revenue. You like it if you burn the same volume every month. If you don't, you're paying for gigabytes you never touch.

**Pay-as-you-go.** You top up a balance and it drains as you use it. No monthly minimum. This is the model that survives uneven workloads, and it's the one where "does my traffic expire?" becomes the single most important question on the page.

That last question is where a lot of the effective markup lives. A provider advertising $1/GB with a 30-day expiry isn't selling you $1/GB. They're selling you $1/GB conditional on you finishing the bag on schedule, and the unused remainder goes back on their books.

## What a fair rate actually looks like

Published proxy pricing guides put the 2026 fair ranges roughly here:

| Proxy type | Typical billing | Fair range |
| --- | --- | --- |
| Residential | Per GB | ~$1–8/GB |
| Datacenter | Per GB or per IP/month | ~$0.50–3/GB, or a few $ per IP/month |
| Mobile (4G/5G) | Per GB or per IP/month | ~$2–15/GB |
| ISP / static residential | Per IP/month | ~$1.50–5/IP/month |
| Managed scraper / SERP APIs | Per 1,000 requests | ~$0.30–12 |

Take the source with the appropriate salt: one of the guides publishing these numbers is DataImpulse's own, and vendors write these pages with their own shelf price in mind. What's useful is the shape of it. Around $1/GB for residential traffic sits at the value end. $3–4/GB is mid-market. $5–8/GB is enterprise pricing, and you should be getting something concrete for the difference, like a dedicated account manager, a signed DPA, or named-account support with an SLA.

Mobile is the expensive lane and it deserves a sanity check before you buy. If your target site doesn't check carrier ASNs, you're paying three to ten times the residential rate for nothing.

## Five things to check before you send money

**1. Does unused traffic expire?** If yes, do the maths on your actual monthly usage, not your best month. A subscription that expires is a floor on your spending whether you use it or not.

**2. What does targeting cost?** Country-level targeting is usually included. State, city, ZIP and ASN filters frequently aren't, and some vendors bill that traffic at a premium rate. On a residential plan where city targeting doubles the per-GB charge, a "city-level scraping project" can cost twice what the headline suggested.

**3. What's the replacement policy for dead IPs?** For per-IP products this matters more than price. Some sellers only replace after a failure threshold, some charge, some replace on request. Ask before, not after.

**4. Which protocols and auth methods?** HTTP, HTTPS and SOCKS5 are the common three. Ask whether SOCKS5 is included in the base plan or an add-on, and whether you get username/password auth, IP whitelisting, or both.

**5. Refund terms, in writing.** Check the conditions attached. Consumption thresholds, payment-method exclusions, and time windows all show up in the fine print.

## Testing a proxy seller in your first 24 hours

Buy the smallest package that lets you run a real test. Not a demo, not a sales call, a small paid pool. Then:

1. Run 100–300 requests per target site you actually care about, not against a generic API.
2. Log median latency, success rate and timeout ratio.
3. Check that the country, city and ASN of the returned IPs match what you were sold. A "US residential" pool that resolves to datacenter ASN ranges is a problem worth catching on day one.
4. Test at the same thread count you'd run in production. Fifty concurrent tasks in the test, not five.
5. Keep raw logs with timestamps and error codes. A support ticket that says "18% timeouts at 40 threads on subnet X" gets resolved faster than "the proxies are bad."

Set your pass/fail rules before the test so you're not arguing with yourself afterwards.

## Where DataImpulse lands on that checklist

DataImpulse is a Cyprus-based proxy provider that third-party reviewers date to 2022, and its pitch is deliberately narrow: residential traffic at $1 per GB, pay-as-you-go, and bytes that never expire. No monthly minimum, no card-on-file requirement to start, no enterprise tier hidden behind a sales qualification call.

The pool is advertised at 90M+ ethically sourced IPs across 195 countries, with HTTP(S) and SOCKS5 both supported, plus rotating and sticky sessions. Sticky sessions run from 1 to 120 minutes with a 30-minute default, which is the range you want if some of your targets behave better with a consistent identity inside a short window. The residential gateway sits at `gw.dataimpulse.com:823`, and country targeting is included in the base rate rather than treated as an upgrade.

TechRadar's review of the service singled out two things: that unexpiring pay-as-you-go traffic separates it from a chunk of the market, and that the $1/GB residential baseline undercuts providers like Bright Data, Oxylabs and Decodo. That's an editorial judgement from an independent review, not a DataImpulse claim, and it's consistent with the pricing that shows up on comparison pages.

Two honest limits on the "no expiry" appeal: it's a real advantage for bursty workloads, and close to irrelevant if you already burn exactly 200 GB every month on the dot. In that case a volume tier is the better lever.

### Every DataImpulse product line, as currently published

DataImpulse doesn't sell named monthly subscriptions. It sells per-GB packages across four product types, with the rate dropping at volume. Here's the full line-up:

| Proxy type | Entry package | Standard rate | Volume rate | Targeting | Start here |
| --- | --- | --- | --- | --- | --- |
| **Residential** — 90M+ IPs, 195 countries, rotating + sticky | $5 for 5 GB | $1/GB | $0.80/GB at 1 TB ($800) | Country included; state/city/ZIP/ASN billed at 2× | [Start with 5 GB of residential traffic](https://bit.ly/dataimPulse) |
| **Datacenter** — high-speed server IPs, 99.9% uptime, randomized subnets | $5 for 10 GB | $0.50/GB | $0.45/GB at 1 TB ($450) | Appears included | [Start with 10 GB of datacenter traffic](https://bit.ly/dataimPulse) |
| **Mobile** — 5G/4G/3G/LTE carrier IPs | $5 for 2.5 GB | $2/GB | $1.60/GB at 1 TB ($1,600) | Country included | [Start with 2.5 GB of mobile traffic](https://bit.ly/dataimPulse) |
| **Premium residential** — high-speed pool, personal account manager | $5 for 1 GB | $5/GB | Custom from $20,000 at 5 TB+ | All options included, no surcharge | [Start with 1 GB of premium residential traffic](https://bit.ly/dataimPulse) |

Above the 1 TB tier, all four lines move to custom pricing: from $2,250 on datacenter at 5 TB+, $8,000 on mobile at 5 TB+, and $20,000 on premium residential at 5 TB+. Traffic doesn't expire on any of them, and there's no subscription attached to any line.

Location counts vary by product: comparison documentation lists 214 locations for residential, 191 for mobile, 123 for datacenter and 210 for premium residential. Worth checking against your target market before you buy rather than after.

## Which line matches your job

**Residential at $1/GB** is the default for anything on a site that inspects IP reputation: e-commerce scraping, SERP tracking, ad verification, price monitoring. If you're unsure, start here. It's the cheapest way to find out whether the pool works on your targets.

**Datacenter at $0.50/GB** is half the residential rate and the right call for bulk crawling, uptime checks and testing workflows where a block or two doesn't destroy the dataset. Then watch your block rate. A cheap plan that fails a third of its requests isn't cheap.

**Mobile at $2/GB** costs double residential, so it needs a reason. Moving through carrier networks where NAT means many users share one IP is that reason. Mobile app testing and targets that are aggressive about residential ranges qualify. Generic scraping doesn't.

**Premium residential at $5/GB** is a five-fold jump, and the pitch is a faster pool with a dedicated account manager and all targeting unlocked. If your budget for a project is $20, you're in the wrong lane. If you're running a production pipeline where a failed request has a real cost attached, the targeting being free matters, since it removes the 2× surcharge on city, ZIP and ASN filters that standard residential carries.

👉 [Test the $5 residential intro package against your own targets](https://bit.ly/dataimPulse)

## Where DataImpulse is the wrong buy

DataImpulse says this itself, and it's worth repeating because it saves time. If you need static ISP proxies, a fully managed scraping API, or you need to access banking and government sites, this isn't the tool. It does rotating residential, mobile and datacenter traffic for collecting public data from public sites. That's the whole product.

Three more practical notes before checkout:

- **There's no free trial.** The minimum spend is $5. The intro plans carry a 7-day money-back guarantee for card payments, conditional on less than 80% of the traffic being consumed. Crypto purchases on intro plans are non-refundable, so if you might want your money back, pay by card.
- **Advanced targeting costs 2× on standard residential.** Budget for it if your project is city- or ZIP-specific. Third-party write-ups specifically recommend confirming current billing treatment on this with support before you commit a big number to it.
- **No KYC gate.** You can register and start without business verification, which is convenient for freelancers and small teams, and the opposite of what enterprise procurement usually wants.

## Quick answers

**Does DataImpulse offer a free trial?**
No. The closest thing is the $5 intro package, which is a paid offer rather than a free trial, with a 7-day money-back guarantee on card payments if you've used less than 80% of the traffic. Compared with providers who run 3–7 day trials gated behind business verification, the practical difference is that there's no clock running on your test.

**Do the gigabytes expire?**
No. Unused traffic stays on your account.

**What's the cheapest way to evaluate it?**
$5 for 5 GB of residential traffic, pointed at your own target sites, with success rate and geo accuracy logged. If residential passes, the datacenter line at $0.50/GB will handle anything that doesn't need residential IPs.

**What should I expect to plug it into?**
Standard HTTP/HTTPS and SOCKS5, with username/password auth or IP whitelisting. That covers the usual scrapers, anti-detect browsers and automation frameworks without extra configuration.

## The short version

The proxy seller question isn't really "who's cheapest per gigabyte." It's whether the rate you're quoted is the rate you'll actually pay once targeting, expiry and replacement policies are priced in.

DataImpulse's offer is easy to evaluate because it's unusually plain: $1/GB residential, $0.50/GB datacenter, $2/GB mobile, $5/GB premium residential, traffic that doesn't expire, no subscription, no business verification, and a $5 entry point across all four lines. Whether that's the right seller for you depends on your targets and your tolerance for advanced-targeting surcharges on standard residential, which is exactly what a $5 test tells you in an afternoon.

👉 [Open a DataImpulse account and run that test](https://bit.ly/dataimPulse)
