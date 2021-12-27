# what are the subscription benefits
- **tier 1**: sock replay/lookup (view history)
- **tier 2**: chat, mute/ban, lookup (view history), hide badges (obscure presence), and all lower tier benefits
- **tier 3**: alias (obscure presence), and all lower tier benefits
- **tier 4**: random username (obscure presence), and all lower tier benefits
- **tier 5**: never write logs + delete logs (destroy history), and all lower tier benefits

# how much do subscriptions cost?
here's the relavent code which generates subscription prices
```python
BASE_PRICE = 500
BULK_MONTH_DISCOUNT_SCALING = {
    1: 1,
    3: 0.9,
    6: 0.8,
}
TIER_SCALING = {
    1: 1,
    2: 2,
    3: 4,
    4: 8,
    5: 16,
}
def sub_price(months: int, tier: int) -> int:
    return round(BASE_PRICE * months * BULK_MONTH_DISCOUNT_SCALING[months] * TIER_SCALING[tier])
```
all subscriptions are in dollars only (why? for convenience) (however donations can be made in any currency)

in the code block the `500` represents 500 cents (United States Dollar)

here's a table of all the possible prices

| months | tier 1 | tier 2 | tier 3 | tier 4 | tier 5 |
| - | - | - | - | - | - |
| 1 | $5.00 | $10.00 | $20.00 | $40.00 | $80.00 |
| 3 | $13.50 | $27.00 | $54.00 | $108.00 | $216.00 |
| 6 | $24.00 | $48.00 | $96.00 | $192.00 | $384.00 |


# does streamforthepeople take a cut?
yes, 15% of subscription fees and 5% of donations (see [philosophy](https://github.com/streamforthepeople/philosophy#streamforthepeoples-cut) for a justification), also note that this is on top of [payment processing fees from stripe](https://stripe.com/pricing)

# will i have to stop using my existing payment portals?
hell no, streamforthepeople is primarily a service *for streamers*, and the payment portals available through it are meant to offer audiences benefits specifically tied to the stream, and are tightly integrated into the website, and the cuts reflect that integration; alternative payment/donation/subscriptions links can be freely presented anywhere on the site (in menu and in tiles) ...

this is identical to how stream service providers already function, you can donate through links in the tiles of twitch or in the youtube description, but these won't be integrated into their site

more broadly this demonstrates what streamforthepeople aims to be in relation to the streamer, their primary, central infrastructure for collecting compensation *surrounding* their stream; certainly the streamer should advertise their compensation links throughout their online presence and maximize the avenues through which they can collect compensation, this avenue is simply integrated tightly with their stream

# won't this split my audience?
to be precise, your **chat** will be split between those that use the stream service provider's chat (e.g. twitch chat, youtube chat, etc.) and those that use the streamer website's chat, we need to understand the implications of this including ways to influence the downsides of it ("dead" chats on the stream service provider side may negatively affect viewership, dead chats on the streamer website chat may make users hesitant to switch over) and ways to address it (i think the best way to handle this is a forwarder for the stream service providers' chats, so the true chat velocity is always maintained, and a toggle-able receiver on the streamer website chat)
