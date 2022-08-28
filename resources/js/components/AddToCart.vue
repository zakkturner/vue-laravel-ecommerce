<template>
    <div>
        <hr />
        <button
            class="btn btn-warning text-center"
            v-on:click.prevent="addProductToCart()"
        >
            Add to Cart
        </button>
    </div>
</template>

<script>
import axios from "axios";

export default {
    data() {},
    props: ["productId", "userId"],
    methods: {
        async addProductToCart() {
            // Check if user is logged in
            if (this.userId == 0) {
                this.$toastr.e(
                    "You Need to login, To add this product in Cart"
                );
                return;
            }
            // if user logged in then add item to cart
            let response = await axios.post("/cart", {
                product_id: this.productId,
            });

            console.log(response);
        },
    },
    mounted() {
        console.log("Component mounted.");
    },
};
</script>
